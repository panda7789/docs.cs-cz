---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: 8f4e415576562885c9edbd3d2dddbe2a271e9923
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005464"
---
# <a name="-libpath"></a>-libpath
Určuje umístění odkazovaných sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-libpath:dirList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`dirList`|Požadováno. Středníkem oddělený seznam adresářů, ve kterých se má kompilátor hledat, pokud odkazované sestavení nebylo nalezeno v aktuálním pracovním adresáři (adresář, ze kterého vyvoláváte kompilátor), nebo systémový adresář společného jazykového modulu runtime. Pokud název adresáře obsahuje mezeru, uzavřete název do uvozovek ("").|  
  
## <a name="remarks"></a>Poznámky  
 Možnost `-libpath` určuje umístění sestavení, na které odkazuje možnost [-reference](../../../visual-basic/reference/command-line-compiler/reference.md) .  
  
 Kompilátor vyhledá odkazy na sestavení, které nejsou plně kvalifikované v následujícím pořadí:  
  
1. Aktuální pracovní adresář. Toto je adresář, ze kterého je kompilátor vyvolán.  
  
2. Systémový adresář společného jazykového modulu runtime.  
  
3. Adresáře určené parametrem `/libpath`.  
  
4. Adresáře určené proměnnou prostředí LIB.  
  
 Možnost `-libpath` je doplňková; zadáním více než jednou se připojí k jakýmkoli předchozím hodnotám.  
  
 K určení odkazu na sestavení použijte `-reference`.  
  
|Nastavení/LIBPATH v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1. v **Průzkumník řešení**mít vybraný projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**. <br />2. klikněte na kartu **odkazy** .<br />3. klikněte na tlačítko **cesty k odkazům...** .<br />4. v dialogovém okně **cesty k odkazům** zadejte název adresáře do pole **Složka:** .<br />5. klikněte na **Přidat složku**.|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` pro vytvoření souboru. exe. Kompilátor bude hledat v pracovním adresáři v kořenovém adresáři jednotky C: a v adresáři New Assemblies (sestavení) na jednotce C: pro odkazy na sestavení.  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Sestavení v .NET](../../../standard/assembly/index.md)
- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
