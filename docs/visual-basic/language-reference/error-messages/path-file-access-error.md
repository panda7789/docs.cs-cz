---
title: Chyba přístupu k cestě nebo k souboru
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: dfe96cd6eaa673438849fe8f799d46fa2617bfdd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387254"
---
# <a name="pathfile-access-error"></a>Chyba přístupu k cestě nebo k souboru
Během operace přístupu k souboru nebo přístupu k disku nemohl operační systém vytvořit spojení mezi cestou a názvem souboru.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Ujistěte se, že specifikace souboru je správně naformátovaná. Název souboru může obsahovat plně kvalifikovanou (absolutní) nebo relativní cestu. Plně kvalifikovaná cesta začíná názvem jednotky (Pokud je cesta na jiné jednotce) a je v ní uvedena explicitní cesta z kořene souboru. Libovolná cesta, která není plně kvalifikovaná, je relativní vzhledem k aktuální jednotce a adresáři.  
  
2. Ujistěte se, že jste se nepokoušeli uložit soubor, který by nahradil existující soubor určený jen pro čtení. Pokud se jedná o tento případ, změňte atribut jen pro čtení cílového souboru nebo uložte soubor s jiným názvem souboru.  
  
3. Ujistěte se, že jste se nepokoušeli otevřít soubor jen pro čtení v sekvenčním `Output` nebo `Append` režimu. Pokud se jedná o tento případ, otevřete soubor v `Input` režimu nebo změňte atribut souboru jen pro čtení.  
  
4. Ujistěte se, že jste se nepokoušeli změnit Visual Basic projekt v rámci databáze nebo dokumentu.  
  
## <a name="see-also"></a>Viz také

- [Typy chyb](../../programming-guide/language-features/error-types.md)
