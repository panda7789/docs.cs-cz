---
title: Procedura přetížení (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- signatures
- Overloads keyword [Visual Basic]
- hiding by signature
- Visual Basic code, procedures
- procedures [Visual Basic], signatures for
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- parameters [Visual Basic], lists
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- Shadows keyword [Visual Basic]
- procedure overloading
- procedures [Visual Basic], parameter lists
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
ms.openlocfilehash: 6e8d1fa72c60c4fa3d2237ad24c2d1b4891a7bf2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828235"
---
# <a name="procedure-overloading-visual-basic"></a>Procedura přetížení (Visual Basic)
*Přetížení* postup znamená, že jeho definováním v více verzí pomocí stejného názvu, ale seznamy různých parametrů. Účelem přetížení je definovat několik úzce související verze procedury, aniž byste museli rozlišit podle názvu. Můžete to provést pomocí různých seznamu parametrů.  
  
## <a name="overloading-rules"></a>Přetížení pravidla  
 Když je přetížení procedury, platí následující pravidla:  
  
-   **Stejný název**. Všechny přetížené verze, musíte použít stejný název procedury.  
  
-   **Jiný podpis**. Všechny přetížené verze se musí lišit od jiných přetížené verze alespoň v jedné z těchto ohledech:  
  
    -   Počet parametrů  
  
    -   Pořadí parametrů  
  
    -   Datové typy parametrů  
  
    -   Počet parametrů typu (pro obecný postup)  
  
    -   Návratový typ (pouze pro operátor převodu)  
  
     Spolu s názvem procedury se společně nazývají předchozí položky *podpis* procedury. Při volání přetížené procedury kompilátor používá ke kontrole, jestli volání správně odpovídá definici podpis.  
  
-   **Položky není součástí podpis**. Bez různé podpis nelze přetížení procedury. Konkrétně se nemůže přetížení procedury změnou pouze jeden nebo více z následujících položek:  
  
    -   Postup modifikátor klíčová slova, jako například `Public`, `Shared`, a `Static`  
  
    -   Názvy parametrů parametru nebo typ  
  
    -   Omezení parametru typu (pro obecný postup)  
  
    -   Klíčová slova modifikátor parametru, jako například `ByRef` a `Optional`  
  
    -   Určuje, zda vrací hodnotu  
  
    -   Datový typ vrácené hodnoty (s výjimkou operátoru převodu)  
  
     Položky v předchozím seznamu nejsou součást podpisu. I když nelze je použít k rozlišení mezi přetížené verze, můžete je lišit mezi přetížené verze, které jsou správně rozlišené pomocí jejich podpisy.  
  
-   **S pozdní vazbou argumenty**. Pokud máte v úmyslu pozdní vazbou objektové proměnné předat přetížené verze, je třeba deklarovat jako odpovídající parametr <xref:System.Object>.  
  
## <a name="multiple-versions-of-a-procedure"></a>Více verzí procedury  
 Předpokládejme, že vytváříte `Sub` postup pro transakci proti zůstatek zákazníka a chtějí mít možnost odkazovat na zákazníka, název nebo číslo účtu. K tomuto účelu můžete definovat dva různé `Sub` postupy, jako v následujícím příkladu:  
  
 [!code-vb[VbVbcnProcedures#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#73)]  
  
### <a name="overloaded-versions"></a>Přetížené verze  
 Alternativou je přetížení název jedinou proceduru. Můžete použít [přetížení](../../../../visual-basic/language-reference/modifiers/overloads.md) – klíčové slovo k definování verzi postup pro každý seznam parametrů, následujícím způsobem:  
  
 [!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]  
  
#### <a name="additional-overloads"></a>Další přetížení  
 Pokud byste chtěli také tak, aby přijímal částka transakce buď `Decimal` nebo `Single`, může další přetížení `post` povolit pro tuto variaci. Pokud jste to udělali u každého z přetížení v předchozím příkladu, byste měli čtyři `Sub` postupy, všechny se stejným názvem, ale s různými signaturami čtyři.  
  
## <a name="advantages-of-overloading"></a>Výhody přetížení  
 Výhodou přetížení procedury je flexibilitu volání. Použít `post` postup deklarované v předchozím příkladu, volající kód může získat Identifikace zákazníka jako buď `String` nebo `Integer`a následně zavolat stejný postup v obou případech. Následující příklad ukazuje toto:  
  
 [!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]  
  
 [!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]  
  
## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Postupy: Definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Postupy: Volání přetížené procedury](./how-to-call-an-overloaded-procedure.md)
- [Postupy: Přetížení procedury, která přebírá volitelné parametry](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Aspekty přetížení procedur](./considerations-in-overloading-procedures.md)
- [Řešení přetížení](./overload-resolution.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Obecné typy v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
