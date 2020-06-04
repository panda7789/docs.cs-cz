---
title: Typ parametru '<parametername>' není kompatibilní se specifikací CLS.
ms.date: 07/20/2015
f1_keywords:
- vbc40028
- bc40028
helpviewer_keywords:
- BC40028
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
ms.openlocfilehash: edbcadf271c4ccafc11e5b64eb103a0290976179
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413011"
---
# <a name="type-of-parameter-parametername-is-not-cls-compliant"></a><span data-ttu-id="40b0a-102">Typ parametru '\<parametername>' není kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="40b0a-102">Type of parameter '\<parametername>' is not CLS-compliant</span></span>
<span data-ttu-id="40b0a-103">Procedura je označena jako `<CLSCompliant(True)>` , ale deklaruje parametr s typem, který je označen jako `<CLSCompliant(False)>` , není označen nebo nesplňuje, protože se jedná o nekompatibilní typ.</span><span class="sxs-lookup"><span data-stu-id="40b0a-103">A procedure is marked as `<CLSCompliant(True)>` but declares a parameter with a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="40b0a-104">Aby byl postup kompatibilní s [nezávislostí jazyka a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), musí používat pouze typy kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="40b0a-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="40b0a-105">To platí pro typy parametrů, návratový typ a typy všech místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="40b0a-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="40b0a-106">Následující Visual Basic datové typy nejsou kompatibilní se specifikací CLS:</span><span class="sxs-lookup"><span data-stu-id="40b0a-106">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="40b0a-107">SByte – datový typ</span><span class="sxs-lookup"><span data-stu-id="40b0a-107">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="40b0a-108">UInteger – datový typ</span><span class="sxs-lookup"><span data-stu-id="40b0a-108">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="40b0a-109">ULong – datový typ</span><span class="sxs-lookup"><span data-stu-id="40b0a-109">ULong Data Type</span></span>](../data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="40b0a-110">UShort – datový typ</span><span class="sxs-lookup"><span data-stu-id="40b0a-110">UShort Data Type</span></span>](../data-types/ushort-data-type.md)  
  
 <span data-ttu-id="40b0a-111">Použijete-li na <xref:System.CLSCompliantAttribute> programovací prvek, nastavíte `isCompliant` parametr atributu na hodnotu `True` nebo `False` k označení dodržování předpisů nebo nedodržení předpisů.</span><span class="sxs-lookup"><span data-stu-id="40b0a-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="40b0a-112">Pro tento parametr neexistuje výchozí hodnota a je třeba uvést hodnotu.</span><span class="sxs-lookup"><span data-stu-id="40b0a-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="40b0a-113">Pokud na prvek nepoužijete <xref:System.CLSCompliantAttribute> , bude považován za nekompatibilní.</span><span class="sxs-lookup"><span data-stu-id="40b0a-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="40b0a-114">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="40b0a-114">By default, this message is a warning.</span></span> <span data-ttu-id="40b0a-115">Informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="40b0a-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="40b0a-116">**ID chyby:** BC40028</span><span class="sxs-lookup"><span data-stu-id="40b0a-116">**Error ID:** BC40028</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="40b0a-117">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="40b0a-117">To correct this error</span></span>  
  
- <span data-ttu-id="40b0a-118">Pokud procedura musí přijmout parametr tohoto konkrétního typu, odeberte <xref:System.CLSCompliantAttribute> .</span><span class="sxs-lookup"><span data-stu-id="40b0a-118">If the procedure must take a parameter of this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="40b0a-119">Procedura nemůže být kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="40b0a-119">The procedure cannot be CLS-compliant.</span></span>  
  
- <span data-ttu-id="40b0a-120">Pokud procedura musí být kompatibilní se specifikací CLS, změňte typ tohoto parametru na nejbližší typ kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="40b0a-120">If the procedure must be CLS-compliant, change the type of this parameter to the closest CLS-compliant type.</span></span> <span data-ttu-id="40b0a-121">Například, `UInteger` `Integer` Pokud nepotřebujete rozsah hodnoty nad 2 147 483 647, můžete použít třeba místo.</span><span class="sxs-lookup"><span data-stu-id="40b0a-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="40b0a-122">Pokud budete potřebovat Rozšířený rozsah, můžete nahradit `UInteger` `Long` .</span><span class="sxs-lookup"><span data-stu-id="40b0a-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="40b0a-123">Pokud procházíte s objekty automatizace nebo COM, pamatujte, že některé typy mají odlišnou šířku dat než v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="40b0a-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="40b0a-124">Například `int` obvykle je 16 bitů v jiných prostředích.</span><span class="sxs-lookup"><span data-stu-id="40b0a-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="40b0a-125">Pokud přijímáte 16bitové celé číslo z takové komponenty, deklarujte ho `Short` místo `Integer` ve spravovaném kódu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="40b0a-125">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>
