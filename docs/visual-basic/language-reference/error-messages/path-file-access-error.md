---
title: Chyba přístupu k souboru v cestě
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: 53f021faa9e4ae69a71d825ca823e1180421afc6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54522476"
---
# <a name="pathfile-access-error"></a>Chyba přístupu k cestě nebo k souboru
Během operace přístupu k souborům nebo přístup k disku operačního systému nelze provést připojení mezi cestu a název souboru.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Ujistěte se, že je správně naformátován specifikace souboru. Název souboru může obsahovat plně kvalifikovanou (absolutní) nebo relativní cestu. Plně kvalifikovaná cesta začíná název jednotky (Pokud se cesta na jiné jednotce) a seznamy explicitních cestu z kořene do souboru. Jakoukoli cestu, která není plně kvalifikovaný je relativní vzhledem k aktuální jednotky a adresáře.  
  
2.  Ujistěte se, že jste se nepokusil uložit soubor, který by nahradit stávající soubor jen pro čtení. Pokud je to tento případ, změnit atribut jen pro čtení cílový soubor nebo uložte soubor s jiným názvem souboru.  
  
3.  Ujistěte se, že nepokusil otevřít soubor jen pro čtení v sekvenčních `Output` nebo `Append` režimu. Pokud je to tento případ, otevřete ho v `Input` režimu nebo změnit atribut jen pro čtení souboru.  
  
4.  Ujistěte se, že se že nepokusil změnit projekt jazyka Visual Basic v databázi nebo dokumentu.  
  
## <a name="see-also"></a>Viz také:
- [Typy chyb](../../../visual-basic/programming-guide/language-features/error-types.md)
