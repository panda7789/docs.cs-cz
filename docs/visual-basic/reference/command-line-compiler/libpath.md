---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: 9a5822a097828f818da020735c3822e86eb3236b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716640"
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
 Možnost `-libpath` určuje umístění sestavení, na která odkazuje možnost [-reference](../../../visual-basic/reference/command-line-compiler/reference.md) .  
  
 Kompilátor vyhledá odkazy na sestavení, které nejsou plně kvalifikované v následujícím pořadí:  
  
1. Aktuální pracovní adresář. Toto je adresář, ze kterého je kompilátor vyvolán.  
  
2. Systémový adresář společného jazykového modulu runtime.  
  
3. Adresáře určené `-libpath`.  
  
4. Adresáře určené proměnnou prostředí LIB.  
  
 Možnost `-libpath` je aditivní; zadáním více než jednou se připojí k jakýmkoli předchozím hodnotám.  
  
 Pomocí `-reference` zadejte odkaz na sestavení.  
  
|Nastavení-LIBPATH v integrovaném vývojovém prostředí sady Visual Studio|  
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
