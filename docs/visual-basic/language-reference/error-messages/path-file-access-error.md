---
title: Chyba přístupu k souboru cesta
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: 83ce8615b173a6f5835347ebc561a793655ec8f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598580"
---
# <a name="pathfile-access-error"></a>Chyba přístupu k cestě nebo k souboru
Během operace přístupu k souborům nebo přístup k disku operačního systému nelze navázat připojení mezi cestu a název souboru.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte, zda že je správně naformátován specifikaci souboru. Název souboru může obsahovat plně kvalifikovaný (absolutní) nebo relativní cestu. Plně kvalifikovaná cesta začíná název jednotky (Pokud je cesta na jiné jednotce) a zobrazuje explicitní cestu z kořene do souboru. Jakoukoli cestu, která není plně kvalifikovaná je relativní vzhledem k aktuální jednotky a adresáře.  
  
2.  Ujistěte se, že jste se nepokusil uložit soubor, který by nahradit existující soubor jen pro čtení. Pokud je to tento případ, měnit atribut jen pro čtení cílový soubor a uložte soubor s jiným názvem souboru.  
  
3.  Zajistěte, aby nepokusil otevřete soubor jen pro čtení v sekvenčních `Output` nebo `Append` režimu. Pokud je to tento případ, otevřete soubor v `Input` režimu nebo změnit atribut jen pro čtení souboru.  
  
4.  Zajistěte, aby že nepokusil změnit projektu jazyka Visual Basic v databázi nebo dokumentu.  
  
## <a name="see-also"></a>Viz také  
 [Typy chyb](../../../visual-basic/programming-guide/language-features/error-types.md)
