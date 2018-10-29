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
ms.openlocfilehash: 2c7fb6c88477899a0cf08a467e8f23d687b90c90
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201896"
---
# <a name="-rootnamespace"></a>-rootnamespace
Určuje obor názvů pro všechny deklarace typů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`namespace`|Název oboru názvů, ve kterém chcete uzavřít všechny deklarace typů pro aktuální projekt.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud používáte spustitelného souboru (Devenv.exe) sady Visual Studio ke kompilaci projektu vytvořeného v integrovaném vývojovém prostředí sady Visual Studio, použijte `-rootnamespace` k určení hodnoty <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> vlastnost. Zobrazit [přepínače příkazového řádku nástroje Devenv](/visualstudio/ide/reference/devenv-command-line-switches) Další informace.  
  
 Použít modul common language runtime MSIL Disassembler (`Ildasm.exe`) Chcete-li zobrazit názvy oborů názvů do výstupního souboru.  
  
|Chcete-li nastavit - rootnamespace v integrovaném vývojovém prostředí sady Visual Studio|  
|---|  
|1.  Mají projekt vybraný v **Průzkumníka řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. <br />2.  Klikněte na tlačítko **aplikace** kartu.<br />3.  Upravte hodnotu v **kořenové Namespace** pole.|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `In.vb` a uzavře všechny deklarace typů v oboru názvů `mynamespace`.  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>Viz také:

- [Kompilátor příkazového řádku jazyka Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
- [Ildasm.exe (IL Disassembler)](../../../framework/tools/ildasm-exe-il-disassembler.md)  
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
