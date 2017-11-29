---
title: /optionstrict
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: /optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f783cc5b20c4fe6d7812a05a66cbc4cdfc0b9395
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="optionstrict"></a>/optionstrict
Vynucuje přísné typ sémantiku jako omezení typu implicitní převody.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/optionstrict[+ | -]  
/optionstrict[:custom]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Volitelné. `/optionstrict+` Možnost omezuje typ implicitní převod. Výchozí hodnota pro tuto možnost je `/optionstrict-`. `/optionstrict+` Možnost je stejný jako `/optionstrict`. Můžete použít pro sémantika projektovou typu.  
  
 `custom`  
 Požadováno. Upozornit, pokud sémantiku striktní jazyk nejsou.  
  
## <a name="remarks"></a>Poznámky  
 Když `/optionstrict+` je platná, pouze rozšiřující převody typu můžete provedeny implicitně. Implicitní zužující převody typu, jako je například přiřazení `Decimal` typ objektu na objekt typu integer, jsou hlášena jako chyby.  
  
 Chcete-li vygenerovat upozornění pro implicitní zužující převody typu, použijte `/optionstrict:custom`. Použití `/nowarn:numberlist` ignorovat konkrétní varování a `/warnaserror:numberlist` zacházet s konkrétní upozornění jako chyby.  
  
### <a name="to-set-optionstrict-in-the-visual-studio-ide"></a>Chcete-li nastavit/optionstrict v integrovaném vývojovém prostředí sady Visual Studio  
  
1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti.** Další informace najdete v tématu [Úvod do Návrhář projektu](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Klikněte **zkompilovat** kartě.  
  
3.  Změňte hodnotu v **možnost striktní** pole.  
  
### <a name="to-set-optionstrict-programmatically"></a>Chcete-li nastavit/optionstrict prostřednictvím kódu programu  
  
-   V tématu [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `Test.vb` pomocí sémantiky striktní typu.  
  
```  
vbc /optionstrict+ test.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)  
 [/ optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)  
 [/ optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)  
 [/ nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)  
 [/ warnaserror (Visual Basic)](../../../visual-basic/reference/command-line-compiler/warnaserror.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Dialogové okno Možnosti výchozí hodnoty, projekty, Visual Basic](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
