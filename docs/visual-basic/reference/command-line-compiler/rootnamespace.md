---
title: /rootnamespace
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b02171b28034d676b7027e96c2c66e36be9ae604
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="rootnamespace"></a>/rootnamespace
Určuje obor názvů pro všechny deklarace typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/rootnamespace:namespace  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termín|Definice|  
|---|---|  
|`namespace`|Název oboru názvů, do kterého chcete uzavřete všechny deklarace typu pro aktuální projekt.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud používáte Visual Studio spustitelný soubor (Devenv.exe) k sestavení projektu vytvořeny v integrovaném vývojovém prostředí sady Visual Studio, použijte `/rootnamespace` zadat hodnotu <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> vlastnost. V tématu [příkazového řádku DEVENV](/visualstudio/ide/reference/devenv-command-line-switches) Další informace.  
  
 Použijte modul common language runtime MSIL Disassembler (`Ildasm.exe`) Chcete-li zobrazit názvy oborů názvů ve výstupním souboru.  
  
|Chcete-li nastavit/RootNamespace v sadě Visual Studio integrované vývojové prostředí|  
|---|  
|1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**. <br />2.  Klikněte **aplikace** kartě.<br />3.  Změňte hodnotu v **kořenové Namespace** pole.|  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `In.vb` a uzavře všechny deklarace typu do oboru názvů `mynamespace`.  
  
```  
vbc /rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Ildasm.exe (IL Disassembler)](https://msdn.microsoft.com/library/f7dy01k1)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
