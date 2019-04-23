---
title: Chyba přístupu k souboru v cestě
ms.date: 07/20/2015
f1_keywords:
- vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
ms.openlocfilehash: 4f18c9216aa24840bc205534a97124d12698cb98
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342151"
---
# <a name="pathfile-access-error"></a>Chyba přístupu k cestě nebo k souboru
Během operace přístupu k souborům nebo přístup k disku operačního systému nelze provést připojení mezi cestu a název souboru.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Ujistěte se, že je správně naformátován specifikace souboru. Název souboru může obsahovat plně kvalifikovanou (absolutní) nebo relativní cestu. Plně kvalifikovaná cesta začíná název jednotky (Pokud se cesta na jiné jednotce) a seznamy explicitních cestu z kořene do souboru. Jakoukoli cestu, která není plně kvalifikovaný je relativní vzhledem k aktuální jednotky a adresáře.  
  
2. Ujistěte se, že jste se nepokusil uložit soubor, který by nahradit stávající soubor jen pro čtení. Pokud je to tento případ, změnit atribut jen pro čtení cílový soubor nebo uložte soubor s jiným názvem souboru.  
  
3. Ujistěte se, že nepokusil otevřít soubor jen pro čtení v sekvenčních `Output` nebo `Append` režimu. Pokud je to tento případ, otevřete ho v `Input` režimu nebo změnit atribut jen pro čtení souboru.  
  
4. Ujistěte se, že se že nepokusil změnit projekt jazyka Visual Basic v databázi nebo dokumentu.  
  
## <a name="see-also"></a>Viz také:

- [Typy chyb](../../../visual-basic/programming-guide/language-features/error-types.md)
