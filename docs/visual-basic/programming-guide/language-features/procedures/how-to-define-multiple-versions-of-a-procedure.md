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
ms.openlocfilehash: baaaca13755b9fdc11308ff3e4df39835dbe466e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980773"
---
# <a name="how-to-define-multiple-versions-of-a-procedure-visual-basic"></a>Postupy: Definice více verzí procedury (Visual Basic)
Můžete definovat postup ve více verzích přidáním *přetížení* jeho pomocí se stejným názvem, ale odlišným seznamem parametrů pro každou verzi. Účelem přetížení je definovat několik úzce související verze procedury, aniž byste museli rozlišit podle názvu.  
  
 Další informace najdete v tématu [přetížení procedury](./procedure-overloading.md).  
  
### <a name="to-define-multiple-versions-of-a-procedure"></a>Chcete-li definovat více verzí procedury  
  
1.  Zápis `Sub` nebo `Function` příkazu deklarace pro jednotlivé verze můžete definovat postup. Použijte stejný název procedury v každé deklaraci.  
  
2.  Předcházet `Sub` nebo `Function` – klíčové slovo v deklaraci s [přetížení](../../../../visual-basic/language-reference/modifiers/overloads.md) – klíčové slovo. Volitelně můžete vynechat `Overloads` v deklaracích, ale pokud je zahrnout v některém z deklarací, je třeba jej zahrnout v každou deklaraci.  
  
3.  Po každé příkazu deklarace napište kód procedury pro zpracování konkrétního případu, pokud volající kód poskytuje argumenty odpovídající seznam parametrů pro tuto verzi. Nemáte k otestování pro parametry, které má zadaný volajícímu kódu. Visual Basic odpovídající verzi procedura předá řízení.  
  
4.  Ukončit všechny verze procedury s `End Sub` nebo `End Function` příkaz podle potřeby.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje `Sub` postup pro transakci proti zůstatku zákazníka. Používá `Overloads` – klíčové slovo definovat dvě verze procedury, ten, který přijímá zákazníka podle názvu a druhé číslo účtu.  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
 Volající kód může získat Identifikace zákazníka jako buď `String` nebo `Integer`a potom pomocí stejné volání příkazu v obou případech.  
  
 Informace o tom, jak volat tyto verze `post` postupu naleznete v tématu [jak: Volání přetížené procedury](./how-to-call-an-overloaded-procedure.md).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Ujistěte se, že všechny přetížené verze má stejný název procedury, ale odlišným seznamem parametrů.  
  
## <a name="see-also"></a>Viz také:
- [Procedury](./index.md)
- [Parametry a argumenty procedury](./procedure-parameters-and-arguments.md)
- [Řešení potíží s procedurami](./troubleshooting-procedures.md)
- [Postupy: Přetížení procedury, která přebírá volitelné parametry](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Aspekty přetížení procedur](./considerations-in-overloading-procedures.md)
- [Řešení přetížení](./overload-resolution.md)
