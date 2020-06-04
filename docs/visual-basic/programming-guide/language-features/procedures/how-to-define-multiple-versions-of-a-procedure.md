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
ms.openlocfilehash: 870a18dbf3a7e28b7d7b612e853beeec6908cf6f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387930"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>Postupy: Definice více verzí procedury (Visual Basic)
Můžete definovat proceduru v několika verzích tím, že je *převedete* pomocí stejného názvu, ale s jiným seznamem parametrů pro každou verzi. Účelem přetížení je definovat několik úzce souvisejících verzí procedury bez nutnosti jejich rozlišení podle názvu.  
  
 Další informace najdete v tématu [přetížení procedury](./procedure-overloading.md).  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>Definování více verzí procedury  
  
1. Zápis `Sub` příkazu nebo `Function` prohlášení pro každou verzi procedury, kterou chcete definovat. Použijte stejný název procedury v každé deklaraci.  
  
2. Před `Sub` klíčovým slovem nebo `Function` v každé deklaraci pomocí klíčového slova [Overloads](../../../language-reference/modifiers/overloads.md) . Volitelně můžete `Overloads` v deklaracích vynechat, ale pokud ji zahrnete do kterékoli deklarace, je nutné ji zahrnout do každé deklarace.  
  
3. Za každý příkaz deklarace, kód procedury zápisu pro zpracování konkrétního případu, kde volající kód dodá argumenty odpovídající seznamu parametrů verze. Nemusíte testovat, které parametry zadal volající kód. Visual Basic předá řízení na vyhovující verzi vašeho postupu.  
  
4. V případě potřeby ukončete jednotlivé verze procedury pomocí `End Sub` `End Function` příkazu nebo.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje `Sub` proceduru pro publikování transakce proti zůstatku zákazníka. Pomocí `Overloads` klíčového slova definuje dvě verze procedury, jednu, která přijímá zákazníka podle názvu a druhý podle čísla účtu.  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 Volající kód může získat identifikaci zákazníka buď jako `String` nebo `Integer` , a pak použít stejný volající příkaz v obou případech.  
  
 Informace o tom, jak zavolat tyto verze `post` procedury, naleznete v tématu [How to: Call a Overloads](./how-to-call-an-overloaded-procedure.md).  
  
## <a name="compile-the-code"></a>Kompilovat kód  
 Ujistěte se, že všechny vaše přetížené verze mají stejný název procedury, ale jiný seznam parametrů.  
  
## <a name="see-also"></a>Viz také

- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Řešení potíží s procedurami](./troubleshooting-procedures.md)
- [Postupy: Přetížení procedury, která přebírá nepovinné parametry](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů.](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Aspekty přetížení procedur](./considerations-in-overloading-procedures.md)
- [Rozlišení přetěžování](./overload-resolution.md)
