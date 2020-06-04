---
title: -baseaddress
ms.date: 08/09/2018
f1_keywords:
- /baseaddress
- baseaddress
helpviewer_keywords:
- -baseaddress compiler option [Visual Basic]
- /baseaddress compiler option [Visual Basic]
- baseaddress compiler option [Visual Basic]
ms.assetid: c982bcf2-46e5-47a2-bc8f-a5cc32b7dc47
ms.openlocfilehash: d241584195da7d6f74b45b191c4f63204c200d45
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357177"
---
# <a name="-baseaddress"></a>-baseaddress
Určuje výchozí základní adresu při vytváření knihovny DLL.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Pojem|Definice|  
|---|---|  
|`address`|Povinná hodnota. Základní adresa knihovny DLL. Tato adresa musí být zadána jako šestnáctkové číslo.|  
  
## <a name="remarks"></a>Poznámky  
 Výchozí základní adresa pro knihovnu DLL je nastavena .NET Framework.  
  
 Uvědomte si, že slovo v této adrese se zaokrouhluje na zaoblené. Pokud například zadáte 0x11110001, je zaokrouhlena na 0x11110000.  
  
 Chcete-li dokončit proces podepisování pro knihovnu DLL, použijte `–R` možnost nástroje pro silný pojmenování (Sn. exe).  
  
 Tato možnost je ignorována, pokud cíl není knihovna DLL.  
  
|Nastavení-BaseAddress v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1. v **Průzkumník řešení**mít vybraný projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**. <br />2. klikněte na kartu **kompilovat** .<br />3. klikněte na tlačítko **Upřesnit**.<br />4. upravte hodnotu v poli **základní adresa knihovny DLL:** . **Poznámka:**      **Základní adresa knihovny DLL:** box je jen pro čtení, pokud cíl není knihovna DLL.|  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [-Target (Visual Basic)](target.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
- [Sn. exe (Nástroj pro silný název)](../../../framework/tools/sn-exe-strong-name-tool.md))
