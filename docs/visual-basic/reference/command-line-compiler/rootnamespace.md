---
title: -rootnamespace
ms.date: 03/13/2018
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
ms.openlocfilehash: 4df4e74fc13c922f51f5b74c3c152bdea28b4431
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005206"
---
# <a name="-rootnamespace"></a>-rootnamespace
Určuje obor názvů pro všechny deklarace typů.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a>Argumenty  
  
|Označení|Definice|  
|---|---|  
|`namespace`|Název oboru názvů, do kterého mají být uzavřeny všechny deklarace typu pro aktuální projekt.|  
  
## <a name="remarks"></a>Poznámky  
 Použijete-li spustitelný soubor sady Visual Studio (devenv. exe) ke kompilaci projektu vytvořeného v integrovaném vývojovém prostředí sady Visual `-rootnamespace` Studio, použijte k určení hodnoty <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> vlastnosti. Další informace najdete v tématu [přepínače příkazového řádku devenv](/visualstudio/ide/reference/devenv-command-line-switches) .  
  
 Použijte modul common language runtime MSIL Disassembler (`Ildasm.exe`) pro zobrazení názvů oborů názvů ve výstupním souboru.  
  
|Nastavení-RootNamespace v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1. v **Průzkumník řešení**mít vybraný projekt. V nabídce **projekt** klikněte na příkaz **vlastnosti**. <br />2. klikněte na kartu **aplikace** .<br />3. upravte hodnotu v poli **kořenový obor názvů** .|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `In.vb` a uzavře všechny deklarace typu v oboru názvů `mynamespace`.  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [Ildasm. exe (IL Disassembler)](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
