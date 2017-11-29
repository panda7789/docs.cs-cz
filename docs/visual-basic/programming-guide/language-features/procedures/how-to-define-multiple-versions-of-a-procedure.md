---
title: "Postupy: Definice více verzí procedury (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1abeaa6806252005dd3abfab3ff60bafa0c0cef1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>Postupy: Definice více verzí procedury (Visual Basic)
Můžete definovat procedury ve více verzí podle *přetížení* jeho pomocí se stejným názvem, ale seznam různých parametrů pro každou verzi. Účelem přetížení je definovat několik úzce související verzí procedury bez nutnosti jejich odlišení podle názvu.  
  
 Další informace najdete v tématu [přetížení procedury](./procedure-overloading.md).  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>Chcete-li definovat více verzí procedury  
  
1.  Zápis `Sub` nebo `Function` příkaz deklarace pro každou verzi postupu chcete definovat. Použijte stejný název procedury v každé deklaraci.  
  
2.  Předcházet `Sub` nebo `Function` – klíčové slovo v každé deklarace s [přetížení](../../../../visual-basic/language-reference/modifiers/overloads.md) – klíčové slovo. Volitelně můžete vynechat `Overloads` v deklaracích, ale pokud můžete zahrnout v některém z deklarací, je třeba jej zahrnout v každé deklaraci.  
  
3.  Následující každý příkaz deklarace napište kód postup pro zpracování konkrétní případ, kdy kód volání poskytuje argumenty odpovídající seznam parametrů této verze. Nemáte k testování pro parametry, které má zadaný kód volání. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]ovládací prvek předává na odpovídající verzi vaší procedury.  
  
4.  Ukončit jednotlivých verzí procedury s `End Sub` nebo `End Function` příkaz podle potřeby.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu definuje `Sub` postup post transakce proti zůstatku zákazníka. Použije `Overloads` – klíčové slovo definovat dvě verze postup, který přijímá zákazník podle názvu a dalších číslem účet.  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]  
  
 Volání kódu můžete získat Identifikace zákazníka jako buď `String` nebo `Integer`a potom pomocí stejné volání příkazu v obou případech.  
  
 Informace o tom, jak volat tyto verze nástroje `post` postupu najdete v části [postupy: volání přetížené procedury](./how-to-call-an-overloaded-procedure.md).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Zajistěte, aby že každý přetížené verze má stejný název postupu, ale seznam různých parametrů.  
  
## <a name="see-also"></a>Viz také  
 [Postupy](./index.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Řešení potíží s procedurami](./troubleshooting-procedures.md)  
 [Postupy: přetížení procedury, která přebírá volitelné parametry](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Postupy: přetížení procedury, která přebírá nekonečný počet parametrů](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Aspekty přetížení procedur](./considerations-in-overloading-procedures.md)  
 [Řešení přetížení](./overload-resolution.md)
