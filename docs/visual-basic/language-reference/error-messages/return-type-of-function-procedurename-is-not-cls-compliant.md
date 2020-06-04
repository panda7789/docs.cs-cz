---
title: Návratový typ funkce '<procedurename>' není kompatibilní se specifikací CLS.
ms.date: 07/20/2015
f1_keywords:
- bc40027
- vbc40027
helpviewer_keywords:
- BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
ms.openlocfilehash: 9cc7e25ef1be21ff2f6a71dcb61bc29ec92da30f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400354"
---
# <a name="return-type-of-function-procedurename-is-not-cls-compliant"></a><span data-ttu-id="d4bc3-102">Návratový typ funkce '\<procedurename>' není kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="d4bc3-102">Return type of function '\<procedurename>' is not CLS-compliant</span></span>
<span data-ttu-id="d4bc3-103">`Function`Procedura je označena jako `<CLSCompliant(True)>` , ale vrací typ, který je označen jako `<CLSCompliant(False)>` , není označen nebo nesplňuje, protože se jedná o nekompatibilní typ.</span><span class="sxs-lookup"><span data-stu-id="d4bc3-103">A `Function` procedure is marked as `<CLSCompliant(True)>` but returns a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="d4bc3-104">Aby byl postup kompatibilní s [nezávislostí jazyka a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), musí používat pouze typy kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="d4bc3-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="d4bc3-105">To platí pro typy parametrů, návratový typ a typy všech místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="d4bc3-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="d4bc3-106">Následující Visual Basic datové typy nejsou kompatibilní se specifikací CLS:</span><span class="sxs-lookup"><span data-stu-id="d4bc3-106">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="d4bc3-107">SByte – datový typ</span><span class="sxs-lookup"><span data-stu-id="d4bc3-107">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="d4bc3-108">UInteger – datový typ</span><span class="sxs-lookup"><span data-stu-id="d4bc3-108">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="d4bc3-109">ULong – datový typ</span><span class="sxs-lookup"><span data-stu-id="d4bc3-109">ULong Data Type</span></span>](../data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="d4bc3-110">UShort – datový typ</span><span class="sxs-lookup"><span data-stu-id="d4bc3-110">UShort Data Type</span></span>](../data-types/ushort-data-type.md)  
  
 <span data-ttu-id="d4bc3-111">Použijete-li na <xref:System.CLSCompliantAttribute> programovací prvek, nastavíte `isCompliant` parametr atributu na hodnotu `True` nebo `False` k označení dodržování předpisů nebo nedodržení předpisů.</span><span class="sxs-lookup"><span data-stu-id="d4bc3-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="d4bc3-112">Pro tento parametr neexistuje výchozí hodnota a je třeba uvést hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d4bc3-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="d4bc3-113">Pokud na prvek nepoužijete <xref:System.CLSCompliantAttribute> , bude považován za nekompatibilní.</span><span class="sxs-lookup"><span data-stu-id="d4bc3-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="d4bc3-114">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="d4bc3-114">By default, this message is a warning.</span></span> <span data-ttu-id="d4bc3-115">Informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d4bc3-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="d4bc3-116">**ID chyby:** BC40027</span><span class="sxs-lookup"><span data-stu-id="d4bc3-116">**Error ID:** BC40027</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d4bc3-117">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="d4bc3-117">To correct this error</span></span>  
  
- <span data-ttu-id="d4bc3-118">Pokud `Function` procedura musí vrátit tento konkrétní typ, odeberte <xref:System.CLSCompliantAttribute> .</span><span class="sxs-lookup"><span data-stu-id="d4bc3-118">If the `Function` procedure must return this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="d4bc3-119">Procedura nemůže být kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="d4bc3-119">The procedure cannot be CLS-compliant.</span></span>  
  
- <span data-ttu-id="d4bc3-120">Pokud `Function` procedura musí být kompatibilní se specifikací CLS, změňte návratový typ na nejbližší typ kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="d4bc3-120">If the `Function` procedure must be CLS-compliant, change the return type to the closest CLS-compliant type.</span></span> <span data-ttu-id="d4bc3-121">Například, `UInteger` `Integer` Pokud nepotřebujete rozsah hodnoty nad 2 147 483 647, můžete použít třeba místo.</span><span class="sxs-lookup"><span data-stu-id="d4bc3-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="d4bc3-122">Pokud budete potřebovat Rozšířený rozsah, můžete nahradit `UInteger` `Long` .</span><span class="sxs-lookup"><span data-stu-id="d4bc3-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="d4bc3-123">Pokud procházíte s objekty automatizace nebo COM, pamatujte, že některé typy mají odlišnou šířku dat než v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d4bc3-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="d4bc3-124">Například `int` obvykle je 16 bitů v jiných prostředích.</span><span class="sxs-lookup"><span data-stu-id="d4bc3-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="d4bc3-125">Pokud pro takovou komponentu vrátíte 16bitové celé číslo, deklarujete ho jako `Short` místo `Integer` ve spravovaném kódu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d4bc3-125">If you are returning a 16-bit integer to such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>
