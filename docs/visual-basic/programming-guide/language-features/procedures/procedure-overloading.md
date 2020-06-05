---
title: Přetížení procedury
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
ms.openlocfilehash: f8accc74fbdd9b1d8cf9bc3d8f6ddd26f73452b8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363873"
---
# <a name="procedure-overloading-visual-basic"></a>Procedura přetížení (Visual Basic)

*Přetížení* procedury znamená, že ji definují v několika verzích se stejným názvem, ale s různými seznamy parametrů. Účelem přetížení je definovat několik úzce souvisejících verzí procedury bez nutnosti jejich rozlišení podle názvu. Provedete to tak, že změníte seznam parametrů.

## <a name="overloading-rules"></a>Pravidla přetížení

Při přetížení procedury platí následující pravidla:

- **Stejný název**. Každá přetížená verze musí používat stejný název procedury.

- **Jiný podpis**. Každá přetížená verze se musí lišit od všech ostatních přetížených verzí alespoň v jednom z následujících hledisek:

  - Počet parametrů

  - Pořadí parametrů

  - Datové typy parametrů

  - Počet parametrů typu (pro obecný postup)

  - Návratový typ (jenom pro operátor převodu)

  Spolu s názvem procedury jsou předchozí položky souhrnně označovány jako *podpis* procedury. Při volání přetížené procedury kompilátor používá signaturu k ověření, že volání správně odpovídá definici.

- **Položky, které nejsou součástí podpisu**. Nemůžete přetížit proceduru bez proměnlivého podpisu. Konkrétně nemůžete přetížit proceduru změnou pouze jedné nebo více z následujících položek:

  - Klíčová slova modifikátoru procedury, například `Public` , `Shared` a`Static`

  - Parametry nebo názvy parametrů typu

  - Omezení parametru typu (pro obecný postup)

  - Klíčová slova modifikátoru parametru, například `ByRef` a`Optional`

  - Bez ohledu na to, zda vrací hodnotu

  - Datový typ návratové hodnoty (s výjimkou operátoru převodu)

  Položky v předchozím seznamu nejsou součástí signatury. I když je nemůžete použít k rozlišení mezi přetíženými verzemi, můžete je měnit mezi přetíženými verzemi, které jsou správně odlišeny svými podpisy.

- **Argumenty s pozdní vazbou**. Pokud máte v úmyslu předat proměnnou s pozdní vazbou objektu do přetížené verze, je nutné deklarovat příslušný parametr jako <xref:System.Object> .

## <a name="multiple-versions-of-a-procedure"></a>Více verzí procedury

Předpokládejme, že píšete `Sub` postup pro publikování transakce proti zůstatku zákazníka a chcete být schopni odkazovat na zákazníka buď podle jména, nebo podle čísla účtu. Chcete-li to přizpůsobit, můžete definovat dva různé `Sub` postupy, jako v následujícím příkladu:

[!code-vb[VbVbcnProcedures#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#73)]

### <a name="overloaded-versions"></a>Přetížené verze

Alternativou je přetížení jednoho názvu procedury. Pomocí klíčového slova [přetížení](../../../language-reference/modifiers/overloads.md) můžete definovat verzi procedury pro každý seznam parametrů následujícím způsobem:

[!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]

#### <a name="additional-overloads"></a>Další přetížení

Pokud jste také chtěli přijmout částku transakce v `Decimal` nebo `Single` , můžete `post` pro tuto variantu použít další přetížení. Pokud jste to nastavili pro každé přetížení v předchozím příkladu, měli byste mít čtyři `Sub` postupy, všechny se stejným názvem, ale se čtyřmi různými podpisy.

## <a name="advantages-of-overloading"></a>Výhody přetížení

Výhodou přetížení procedury je flexibilita volání. Chcete-li použít `post` proceduru deklarovanou v předchozím příkladu, volající kód může získat identifikaci zákazníka buď jako `String` nebo `Integer` , a pak zavolat stejný postup v obou případech. Ilustruje to následující příklad:

[!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]

[!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]

## <a name="see-also"></a>Viz také

- [Procedury](./index.md)
- [Postupy: Definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Postupy: Volání přetížené procedury](./how-to-call-an-overloaded-procedure.md)
- [Postupy: Přetížení procedury, která přebírá nepovinné parametry](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů.](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Aspekty přetížení procedur](./considerations-in-overloading-procedures.md)
- [Rozlišení přetěžování](./overload-resolution.md)
- [Přetížení](../../../language-reference/modifiers/overloads.md)
- [Obecné typy v Visual Basic](../data-types/generic-types.md)
