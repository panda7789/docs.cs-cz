---
title: 'Postupy: Vytvoření procedury'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: a831814c18f97991fca8067f1c9c8e491da1b665
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344912"
---
# <a name="how-to-create-a-procedure-visual-basic"></a>Postupy: Vytvoření procedury (Visual Basic)

Můžete uzavřít postup mezi příkazem počáteční deklarace (`Sub` nebo `Function`) a koncovým příkazem deklarace (`End Sub` nebo `End Function`). Mezi těmito příkazy leží celý kód procedury.

 Procedura nemůže obsahovat jinou proceduru, takže její počáteční a koncové příkazy musí být mimo jiné procedury.

 Pokud máte kód, který provádí stejnou úlohu na různých místech, můžete napsat úlohu jednou jako proceduru a potom ji volat z různých míst v kódu.

### <a name="to-create-a-procedure-that-does-not-return-a-value"></a>Vytvoření procedury, která nevrací hodnotu

1. Mimo jakýkoli jiný postup použijte příkaz `Sub` následovaný příkazem `End Sub`.

2. V příkazu `Sub` použijte klíčové slovo `Sub` s názvem procedury a pak seznam parametrů v závorkách.

3. Umístěte příkazy kódu procedury mezi příkazy `Sub` a `End Sub`.

### <a name="to-create-a-procedure-that-returns-a-value"></a>Vytvoření procedury, která vrátí hodnotu

1. Mimo jakýkoli jiný postup použijte příkaz `Function` následovaný příkazem `End Function`.

2. V příkazu `Function` postupujte podle klíčového slova `Function` s názvem procedury, potom seznamem parametrů v závorkách a potom klauzule `As` určující datový typ vrácené hodnoty.

3. Umístěte příkazy kódu procedury mezi příkazy `Function` a `End Function`.

4. Použijte příkaz `Return` pro návrat hodnoty do kódu volajícího.

### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a>Připojení nové procedury se starými, opakujícími se bloky kódu

1. Ujistěte se, že jste definovali nový postup na místě, kde k němu má starý kód.

2. V původním, opakovaném bloku kódu nahraďte příkazy, které provádějí opakující se úkol, jediným příkazem, který volá `Sub` nebo `Function` procedura.

3. Pokud je procedura `Function`, která vrací hodnotu, zajistěte, aby váš volající příkaz prováděl akci s vrácenou hodnotou, jako je například uložení v proměnné, nebo jinak hodnota bude ztracena.

## <a name="example"></a>Příklad

 Následující `Function` postup vypočítá nejdelší stranu (neboli přepony) pravého trojúhelníku s ohledem na hodnoty ostatních dvou stran:

 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

## <a name="see-also"></a>Viz také:

- [Procedury](index.md)
- [Procedury Sub](sub-procedures.md)
- [Procedury funkce](function-procedures.md)
- [Procedury vlastnosti](property-procedures.md)
- [Procedury operátoru](operator-procedures.md)
- [Parametry a argumenty procedury](procedure-parameters-and-arguments.md)
- [Rekurzivní procedury](recursive-procedures.md)
- [Přetížení procedury](procedure-overloading.md)
- [Objekty a třídy](../objects-and-classes/index.md)
- [Objektově orientované programování (Visual Basic)](../../concepts/object-oriented-programming.md)
