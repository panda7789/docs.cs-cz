---
title: "Chyba přístupu k souboru cesta"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID75
ms.assetid: 6ce3a161-7316-46bd-a785-0d50e5414020
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c86d46c884617be152a5954426e9ddd6ef61651
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="pathfile-access-error"></a>Chyba přístupu k cestě nebo k souboru
Během operace přístupu k souborům nebo přístup k disku operačního systému nelze navázat připojení mezi cestu a název souboru.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte, zda že je správně naformátován specifikaci souboru. Název souboru může obsahovat plně kvalifikovaný (absolutní) nebo relativní cestu. Plně kvalifikovaná cesta začíná název jednotky (Pokud je cesta na jiné jednotce) a zobrazuje explicitní cestu z kořene do souboru. Jakoukoli cestu, která není plně kvalifikovaná je relativní vzhledem k aktuální jednotky a adresáře.  
  
2.  Ujistěte se, že jste se nepokusil uložit soubor, který by nahradit existující soubor jen pro čtení. Pokud je to tento případ, měnit atribut jen pro čtení cílový soubor a uložte soubor s jiným názvem souboru.  
  
3.  Zajistěte, aby nepokusil otevřete soubor jen pro čtení v sekvenčních `Output` nebo `Append` režimu. Pokud je to tento případ, otevřete soubor v `Input` režimu nebo změnit atribut jen pro čtení souboru.  
  
4.  Zajistěte, aby pokus o změnu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projektu v databázi nebo dokumentu.  
  
## <a name="see-also"></a>Viz také  
 [Typy chyb](../../../visual-basic/programming-guide/language-features/error-types.md)
