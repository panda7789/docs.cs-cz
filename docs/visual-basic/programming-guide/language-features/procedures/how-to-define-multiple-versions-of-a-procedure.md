---
title: 'Postupy: Definice více verzí procedury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: a4d0c5bbb07dd5433ff62179fc10a6274bf19364
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>Postupy: Definice více verzí procedury (Visual Basic)
Můžete definovat procedury ve více verzí podle *přetížení* jeho pomocí se stejným názvem, ale seznam různých parametrů pro každou verzi. Účelem přetížení je definovat několik úzce související verzí procedury bez nutnosti jejich odlišení podle názvu.  
  
 Další informace najdete v tématu [přetížení procedury](./procedure-overloading.md).  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>Chcete-li definovat více verzí procedury  
  
1.  Zápis `Sub` nebo `Function` příkaz deklarace pro každou verzi postupu chcete definovat. Použijte stejný název procedury v každé deklaraci.  
  
2.  Předcházet `Sub` nebo `Function` – klíčové slovo v každé deklarace s [přetížení](../../../../visual-basic/language-reference/modifiers/overloads.md) – klíčové slovo. Volitelně můžete vynechat `Overloads` v deklaracích, ale pokud můžete zahrnout v některém z deklarací, je třeba jej zahrnout v každé deklaraci.  
  
3.  Následující každý příkaz deklarace napište kód postup pro zpracování konkrétní případ, kdy kód volání poskytuje argumenty odpovídající seznam parametrů této verze. Nemáte k testování pro parametry, které má zadaný kód volání. Visual Basic předá řízení na odpovídající verzi vaší procedury.  
  
4.  Ukončit jednotlivých verzí procedury s `End Sub` nebo `End Function` příkaz podle potřeby.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu definuje `Sub` postup post transakce proti zůstatku zákazníka. Použije `Overloads` – klíčové slovo definovat dvě verze postup, který přijímá zákazník podle názvu a dalších číslem účet.  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/how-to-define-multiple-versions-of-a-procedure_1.vb)]  
  
 Volání kódu můžete získat Identifikace zákazníka jako buď `String` nebo `Integer`a potom pomocí stejné volání příkazu v obou případech.  
  
 Informace o tom, jak volat tyto verze nástroje `post` postupu najdete v části [postupy: volání přetížené procedury](./how-to-call-an-overloaded-procedure.md).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Zajistěte, aby že každý přetížené verze má stejný název postupu, ale seznam různých parametrů.  
  
## <a name="see-also"></a>Viz také  
 [Procedury](./index.md)  
 [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)  
 [Řešení potíží s procedurami](./troubleshooting-procedures.md)  
 [Postupy: Přetížení procedury, která přebírá nepovinné parametry](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [Aspekty přetížení procedur](./considerations-in-overloading-procedures.md)  
 [Řešení přetížení](./overload-resolution.md)
