---
title: Ordinální číslo není platné.
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 7b9bd8435b56dd5e33d14eb35d76aacc7d60c8b5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413050"
---
# <a name="ordinal-is-not-valid"></a>Ordinální číslo není platné.
Vaše volání dynamické knihovny (DLL) označené k použití čísla namísto názvu procedury, pomocí `#num` syntaxe. Tato chyba má následující možné příčiny:  
  
- Pokus o převod `#num` výrazu na pořadové číslo se nezdařil.  
  
- `#num`Zadaný parametr neurčuje žádné funkce v knihovně DLL.  
  
- Knihovna typů má neplatnou deklaraci, která má za následek interní použití neplatného pořadového čísla.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Ujistěte se, že výraz představuje platné číslo, nebo zavolejte proceduru podle názvu.  
  
2. Ujistěte se, že `#num` je v knihovně DLL identifikována platná funkce.  
  
3. Izolujte volání procedury způsobující problém pomocí komentáře kódu. Zápis `Declare` příkazu pro proceduru a nahlášení problému na dodavatele knihovny typů.  
  
## <a name="see-also"></a>Viz také

- [Declare – příkaz](../statements/declare-statement.md)
