---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
ms.openlocfilehash: b7bfcb0f2034145822922126fe61efea8d8ef269
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793923"
---
# <a name="-libpath"></a>-libpath
Určuje umístění odkazovaných sestavení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-libpath:dirList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`dirList`|Povinný parametr. Středníkem oddělený seznam adresářů pro kompilátor hledat v případě odkazovaných sestavení není nalezen v aktuálním pracovním adresáři (adresář, ze kterého je vyvolán kompilátor) nebo systémový adresář common language runtime. Pokud název adresáře obsahuje mezery, uzavřete název do uvozovek ("").|  
  
## <a name="remarks"></a>Poznámky  
 `-libpath` Určuje umístění sestavení odkazuje [– referenční dokumentace](../../../visual-basic/reference/command-line-compiler/reference.md) možnost.  
  
 Kompilátor vyhledá odkazy na sestavení, které nejsou plně kvalifikovaný v následujícím pořadí:  
  
1. Aktuální pracovní adresář. Toto je adresář, ze kterého je vyvolán kompilátor.  
  
2. Common language runtime systémový adresář.  
  
3. Adresáře určeného `/libpath`.  
  
4. Adresáře určené proměnnou prostředí LIB.  
  
 `-libpath` Možnost je sčítání; zadání více než jednou připojí k jakékoli předchozí hodnoty ho.  
  
 Použití `-reference` zadat odkaz na sestavení.  
  
|Chcete-li nastavit/Libpath v sadě Visual Studio integrované vývojové prostředí|  
|---|  
|1.  Mají projekt vybraný v **Průzkumníka řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. <br />2.  Klikněte na tlačítko **odkazy** kartu.<br />3.  Klikněte na tlačítko **odkazují na cesty...**  tlačítko.<br />4.  V **cesty odkazů** dialogového okna zadejte název adresáře v **složky:** pole.<br />5.  Klikněte na tlačítko **přidat složku**.|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` vytvořte soubor s příponou .exe. Kompilátor vyhledá v pracovním adresáři, v kořenovém adresáři jednotky C: a v adresáři nové sestavení jednotce C: pro odkazy na sestavení.  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Sestavení v .NET](../../../standard/assembly/index.md)
- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
