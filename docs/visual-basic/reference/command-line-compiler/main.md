---
title: /main
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c5bb11bc62e951339113f4b48e98e05362490ca1
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="main"></a>/main
Určuje třídu nebo modul, který obsahuje `Sub Main` postupu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/main:location  
```  
  
## <a name="arguments"></a>Arguments  
 `location`  
 Požadováno. Úplné kvalifikace ke třídě nebo modul, který obsahuje `Sub Main` postupu, která se má volat při spuštění programu. To může být ve tvaru **/main:module** nebo **/main:namespace.module**.  
  
## <a name="remarks"></a>Poznámky  
 Tuto možnost použijte, když vytvoříte spustitelného souboru nebo spustitelný program Windows. Pokud **/main** není zadán parametr, kompilátor hledá platný sdílené `Sub Main` v všechny veřejné třídy a moduly.  
  
 V tématu [hlavní procedura v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) diskuzi o různé formy `Main` postupu.  
  
 Když `location` je třída, která dědí z <xref:System.Windows.Forms.Form>, kompilátor poskytuje výchozí `Main` procedury, která spustí aplikaci, pokud třída nemá žádné `Main` postupu. Díky tomu můžete zkompilovat kód na příkazovém řádku, který byl vytvořen ve vývojovém prostředí.  
  
 [!code-vb[VbVbalrCompiler#16](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]  
  
### <a name="to-set-main-in-the-visual-studio-integrated-development-environment"></a>Chcete-li nastavit/Main v sadě Visual Studio integrované vývojové prostředí  
  
1.  Máte projekt vybraný v **Průzkumníku řešení**. Na **projektu** nabídky, klikněte na tlačítko **vlastnosti**.  
  
       
  
2.  Klikněte **aplikace** kartě.  
  
3.  Zajistěte, aby **Povolit aplikační rozhraní** není zaškrtnuto zaškrtávací políčko.  
  
4.  Změňte hodnotu v **spouštěcí objekt** pole.  
  
## <a name="example"></a>Příklad  
 Následující kód zkompiluje `T2.vb` a `T3.vb`, zadání, `Sub Main` najdete postup ve `Test2` třídy.  
  
```  
vbc t2.vb t3.vb /main:Test2  
```  
  
## <a name="see-also"></a>Viz také  
 [Visual Basic – kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Hlavní procedura v jazyce Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
