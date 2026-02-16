from __future__ import annotations
import time
from functools import wraps


# --------- Décorateurs ---------
def timer(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        start = time.perf_counter()
        result = func(*args, **kwargs)
        end = time.perf_counter()
        print(f"[TIMER] {func.__name__} : {(end - start):.6f}s")
        return result
    return wrapper


def log_call(func):
    @wraps(func)
    def wrapper(*args, **kwargs):
        print(f"[LOG] Appel {func.__name__}(args={args}, kwargs={kwargs})")
        return func(*args, **kwargs)
    return wrapper


# --------- César sophistiqué ---------
def _shift_char(c: str, k: int) -> str:
    """Décale une lettre en gardant la casse. Ne modifie pas les non-lettres."""
    if "A" <= c <= "Z":
        return chr((ord(c) - ord("A") + k) % 26 + ord("A"))
    if "a" <= c <= "z":
        return chr((ord(c) - ord("a") + k) % 26 + ord("a"))
    return c  # espaces, ponctuation, chiffres, accents… inchangés


@log_call
@timer
def chiffrer(message: str, decalage: int) -> str:
    return "".join(_shift_char(c, decalage) for c in message)


@log_call
@timer
def dechiffrer(message: str, decalage: int) -> str:
    return "".join(_shift_char(c, -decalage) for c in message)


@log_call
@timer
def chiffrer_fichier(entree: str, sortie: str, decalage: int) -> None:
    with open(entree, "r", encoding="utf-8") as f:
        contenu = f.read()
    chiffre = chiffrer(contenu, decalage)
    with open(sortie, "w", encoding="utf-8") as f:
        f.write(chiffre)


@log_call
@timer
def dechiffrer_fichier(entree: str, sortie: str, decalage: int) -> None:
    with open(entree, "r", encoding="utf-8") as f:
        contenu = f.read()
    clair = dechiffrer(contenu, decalage)
    with open(sortie, "w", encoding="utf-8") as f:
        f.write(clair)


if __name__ == "__main__":
    # Tests rapides
    print(chiffrer("Bonjour, Zzz! 123", 3))     # E rq... + Z->C
    print(dechiffrer("Erqmrxu", 3))            # BONJOUR si c'était en majuscules à la base

    # Test fichier (à adapter avec tes noms de fichiers)
    # chiffrer_fichier("message.txt", "message_chiffre.txt", 3)
    # dechiffrer_fichier("message_chiffre.txt", "message_dechiffre.txt", 3)
