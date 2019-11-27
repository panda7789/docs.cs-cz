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
# <a name="how-to-create-a-procedure-visual-basic"></a><span data-ttu-id="7ecca-102">Postupy: Vytvoření procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ecca-102">How to: Create a Procedure (Visual Basic)</span></span>

<span data-ttu-id="7ecca-103">Můžete uzavřít postup mezi příkazem počáteční deklarace (`Sub` nebo `Function`) a koncovým příkazem deklarace (`End Sub` nebo `End Function`).</span><span class="sxs-lookup"><span data-stu-id="7ecca-103">You enclose a procedure between a starting declaration statement (`Sub` or `Function`) and an ending declaration statement (`End Sub` or `End Function`).</span></span> <span data-ttu-id="7ecca-104">Mezi těmito příkazy leží celý kód procedury.</span><span class="sxs-lookup"><span data-stu-id="7ecca-104">All the procedure's code lies between these statements.</span></span>

 <span data-ttu-id="7ecca-105">Procedura nemůže obsahovat jinou proceduru, takže její počáteční a koncové příkazy musí být mimo jiné procedury.</span><span class="sxs-lookup"><span data-stu-id="7ecca-105">A procedure cannot contain another procedure, so its starting and ending statements must be outside any other procedure.</span></span>

 <span data-ttu-id="7ecca-106">Pokud máte kód, který provádí stejnou úlohu na různých místech, můžete napsat úlohu jednou jako proceduru a potom ji volat z různých míst v kódu.</span><span class="sxs-lookup"><span data-stu-id="7ecca-106">If you have code that performs the same task in different places, you can write the task once as a procedure and then call it from different places in your code.</span></span>

### <a name="to-create-a-procedure-that-does-not-return-a-value"></a><span data-ttu-id="7ecca-107">Vytvoření procedury, která nevrací hodnotu</span><span class="sxs-lookup"><span data-stu-id="7ecca-107">To create a procedure that does not return a value</span></span>

1. <span data-ttu-id="7ecca-108">Mimo jakýkoli jiný postup použijte příkaz `Sub` následovaný příkazem `End Sub`.</span><span class="sxs-lookup"><span data-stu-id="7ecca-108">Outside any other procedure, use a `Sub` statement, followed by an `End Sub` statement.</span></span>

2. <span data-ttu-id="7ecca-109">V příkazu `Sub` použijte klíčové slovo `Sub` s názvem procedury a pak seznam parametrů v závorkách.</span><span class="sxs-lookup"><span data-stu-id="7ecca-109">In the `Sub` statement, follow the `Sub` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>

3. <span data-ttu-id="7ecca-110">Umístěte příkazy kódu procedury mezi příkazy `Sub` a `End Sub`.</span><span class="sxs-lookup"><span data-stu-id="7ecca-110">Place the procedure's code statements between the `Sub` and `End Sub` statements.</span></span>

### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="7ecca-111">Vytvoření procedury, která vrátí hodnotu</span><span class="sxs-lookup"><span data-stu-id="7ecca-111">To create a procedure that returns a value</span></span>

1. <span data-ttu-id="7ecca-112">Mimo jakýkoli jiný postup použijte příkaz `Function` následovaný příkazem `End Function`.</span><span class="sxs-lookup"><span data-stu-id="7ecca-112">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>

2. <span data-ttu-id="7ecca-113">V příkazu `Function` postupujte podle klíčového slova `Function` s názvem procedury, potom seznamem parametrů v závorkách a potom klauzule `As` určující datový typ vrácené hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7ecca-113">In the `Function` statement, follow the `Function` keyword with the name of the procedure, then the parameter list in parentheses, and then an `As` clause specifying the data type of the return value.</span></span>

3. <span data-ttu-id="7ecca-114">Umístěte příkazy kódu procedury mezi příkazy `Function` a `End Function`.</span><span class="sxs-lookup"><span data-stu-id="7ecca-114">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>

4. <span data-ttu-id="7ecca-115">Použijte příkaz `Return` pro návrat hodnoty do kódu volajícího.</span><span class="sxs-lookup"><span data-stu-id="7ecca-115">Use a `Return` statement to return the value to the calling code.</span></span>

### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a><span data-ttu-id="7ecca-116">Připojení nové procedury se starými, opakujícími se bloky kódu</span><span class="sxs-lookup"><span data-stu-id="7ecca-116">To connect your new procedure with the old, repetitive blocks of code</span></span>

1. <span data-ttu-id="7ecca-117">Ujistěte se, že jste definovali nový postup na místě, kde k němu má starý kód.</span><span class="sxs-lookup"><span data-stu-id="7ecca-117">Make sure you define the new procedure in a place where the old code has access to it.</span></span>

2. <span data-ttu-id="7ecca-118">V původním, opakovaném bloku kódu nahraďte příkazy, které provádějí opakující se úkol, jediným příkazem, který volá `Sub` nebo `Function` procedura.</span><span class="sxs-lookup"><span data-stu-id="7ecca-118">In your old, repetitive code block, replace the statements that perform the repetitive task with a single statement that calls the `Sub` or `Function` procedure.</span></span>

3. <span data-ttu-id="7ecca-119">Pokud je procedura `Function`, která vrací hodnotu, zajistěte, aby váš volající příkaz prováděl akci s vrácenou hodnotou, jako je například uložení v proměnné, nebo jinak hodnota bude ztracena.</span><span class="sxs-lookup"><span data-stu-id="7ecca-119">If your procedure is a `Function` that returns a value, ensure that your calling statement performs an action with the returned value, such as storing it in a variable, or else the value will be lost.</span></span>

## <a name="example"></a><span data-ttu-id="7ecca-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="7ecca-120">Example</span></span>

 <span data-ttu-id="7ecca-121">Následující `Function` postup vypočítá nejdelší stranu (neboli přepony) pravého trojúhelníku s ohledem na hodnoty ostatních dvou stran:</span><span class="sxs-lookup"><span data-stu-id="7ecca-121">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides:</span></span>

 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="7ecca-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7ecca-122">See also</span></span>

- [<span data-ttu-id="7ecca-123">Procedury</span><span class="sxs-lookup"><span data-stu-id="7ecca-123">Procedures</span></span>](index.md)
- [<span data-ttu-id="7ecca-124">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="7ecca-124">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="7ecca-125">Procedury funkce</span><span class="sxs-lookup"><span data-stu-id="7ecca-125">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="7ecca-126">Procedury vlastnosti</span><span class="sxs-lookup"><span data-stu-id="7ecca-126">Property Procedures</span></span>](property-procedures.md)
- [<span data-ttu-id="7ecca-127">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="7ecca-127">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="7ecca-128">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="7ecca-128">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="7ecca-129">Rekurzivní procedury</span><span class="sxs-lookup"><span data-stu-id="7ecca-129">Recursive Procedures</span></span>](recursive-procedures.md)
- [<span data-ttu-id="7ecca-130">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="7ecca-130">Procedure Overloading</span></span>](procedure-overloading.md)
- [<span data-ttu-id="7ecca-131">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="7ecca-131">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="7ecca-132">Objektově orientované programování (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ecca-132">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
