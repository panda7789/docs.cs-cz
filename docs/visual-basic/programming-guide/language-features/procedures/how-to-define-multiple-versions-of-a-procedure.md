---
title: 'Postupy: Definice více verzí procedury'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- procedure overloading [Visual Basic], multiple versions
ms.assetid: 71ccdd66-1b00-4b66-bee4-6926c0d696f4
ms.openlocfilehash: 83e96e271f6613aa325d59a0ca2fce9fc69fe059
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350489"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>Postupy: Definice více verzí procedury (Visual Basic)
Můžete definovat proceduru v několika verzích tím, že je *převedete* pomocí stejného názvu, ale s jiným seznamem parametrů pro každou verzi. Účelem přetížení je definovat několik úzce souvisejících verzí procedury bez nutnosti jejich rozlišení podle názvu.  
  
 Další informace najdete v tématu [přetížení procedury](./procedure-overloading.md).  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>Definování více verzí procedury  
  
1. Zápis příkazu `Sub` nebo `Function` deklarace pro každou verzi procedury, kterou chcete definovat. Použijte stejný název procedury v každé deklaraci.  
  
2. Před klíčovým slovem `Sub` nebo `Function` v každé deklaraci uveďte klíčové slovo [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) . Volitelně můžete `Overloads` v deklaracích vynechat, ale pokud ji zahrnete do kterékoli deklarace, je nutné ji zahrnout do každé deklarace.  
  
3. Za každý příkaz deklarace, kód procedury zápisu pro zpracování konkrétního případu, kde volající kód dodá argumenty odpovídající seznamu parametrů verze. Nemusíte testovat, které parametry zadal volající kód. Visual Basic předá řízení na vyhovující verzi vašeho postupu.  
  
4. V případě potřeby ukončete jednotlivé verze postupu pomocí příkazu `End Sub` nebo `End Function`.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje `Sub` postup pro publikování transakce proti zůstatku zákazníka. Pomocí klíčového slova `Overloads` definuje dvě verze procedury, jednu, která přijímá zákazníka podle názvu a druhý podle čísla účtu.  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 Volající kód může získat identifikaci zákazníka jako `String` nebo `Integer`a pak použít stejný volající příkaz v obou případech.  
  
 Informace o tom, jak volat tyto verze `post` postupu, naleznete v tématu [How to: Calling a reloadd](./how-to-call-an-overloaded-procedure.md).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Ujistěte se, že všechny vaše přetížené verze mají stejný název procedury, ale jiný seznam parametrů.  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Řešení potíží s procedurami](./troubleshooting-procedures.md)
- [Postupy: Přetížení procedury, která přebírá nepovinné parametry](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Aspekty přetížení procedur](./considerations-in-overloading-procedures.md)
- [Řešení přetížení](./overload-resolution.md)
