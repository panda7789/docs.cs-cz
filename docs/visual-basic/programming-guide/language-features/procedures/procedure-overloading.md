---
title: Procedura přetížení
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
ms.openlocfilehash: 41a971896fe726cbe9849fd46334910e7288afe0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352590"
---
# <a name="procedure-overloading-visual-basic"></a>Procedura přetížení (Visual Basic)

*Overloading* a procedure means defining it in multiple versions, using the same name but different parameter lists. The purpose of overloading is to define several closely related versions of a procedure without having to differentiate them by name. You do this by varying the parameter list.

## <a name="overloading-rules"></a>Overloading Rules

When you overload a procedure, the following rules apply:

- **Same Name**. Each overloaded version must use the same procedure name.

- **Different Signature**. Each overloaded version must differ from all other overloaded versions in at least one of the following respects:

  - Number of parameters

  - Order of the parameters

  - Data types of the parameters

  - Number of type parameters (for a generic procedure)

  - Return type (only for a conversion operator)

  Together with the procedure name, the preceding items are collectively called the *signature* of the procedure. When you call an overloaded procedure, the compiler uses the signature to check that the call correctly matches the definition.

- **Items Not Part of Signature**. You cannot overload a procedure without varying the signature. In particular, you cannot overload a procedure by varying only one or more of the following items:

  - Procedure modifier keywords, such as `Public`, `Shared`, and `Static`

  - Parameter or type parameter names

  - Type parameter constraints (for a generic procedure)

  - Parameter modifier keywords, such as `ByRef` and `Optional`

  - Whether it returns a value

  - The data type of the return value (except for a conversion operator)

  The items in the preceding list are not part of the signature. Although you cannot use them to differentiate between overloaded versions, you can vary them among overloaded versions that are properly differentiated by their signatures.

- **Late-Bound Arguments**. If you intend to pass a late bound object variable to an overloaded version, you must declare the appropriate parameter as <xref:System.Object>.

## <a name="multiple-versions-of-a-procedure"></a>Multiple Versions of a Procedure

Suppose you are writing a `Sub` procedure to post a transaction against a customer's balance, and you want to be able to refer to the customer either by name or by account number. To accommodate this, you can define two different `Sub` procedures, as in the following example:

[!code-vb[VbVbcnProcedures#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#73)]

### <a name="overloaded-versions"></a>Overloaded Versions

An alternative is to overload a single procedure name. You can use the [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) keyword to define a version of the procedure for each parameter list, as follows:

[!code-vb[VbVbcnProcedures#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#72)]

#### <a name="additional-overloads"></a>Additional Overloads

If you also wanted to accept a transaction amount in either `Decimal` or `Single`, you could further overload `post` to allow for this variation. If you did this to each of the overloads in the preceding example, you would have four `Sub` procedures, all with the same name but with four different signatures.

## <a name="advantages-of-overloading"></a>Advantages of Overloading

The advantage of overloading a procedure is in the flexibility of the call. To use the `post` procedure declared in the preceding example, the calling code can obtain the customer identification as either a `String` or an `Integer`, and then call the same procedure in either case. The following example illustrates this:

[!code-vb[VbVbcnProcedures#56](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#56)]

[!code-vb[VbVbcnProcedures#57](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#57)]

## <a name="see-also"></a>Viz také:

- [Procedury](./index.md)
- [Postupy: Definice více verzí procedury](./how-to-define-multiple-versions-of-a-procedure.md)
- [Postupy: Volání přetížené procedury](./how-to-call-an-overloaded-procedure.md)
- [Postupy: Přetížení procedury, která přebírá nepovinné parametry](./how-to-overload-a-procedure-that-takes-optional-parameters.md)
- [Postupy: Přetížení procedury, která přebírá nekonečný počet parametrů](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)
- [Aspekty přetížení procedur](./considerations-in-overloading-procedures.md)
- [Řešení přetížení](./overload-resolution.md)
- [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)
- [Generic Types in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
