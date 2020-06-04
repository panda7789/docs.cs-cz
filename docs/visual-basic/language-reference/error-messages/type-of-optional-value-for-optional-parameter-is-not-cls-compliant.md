---
title: Typ nepovinné hodnoty pro volitelný parametr <parametername> není kompatibilní se specifikací CLS.
ms.date: 07/20/2015
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords:
- BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
ms.openlocfilehash: 8e53d036ead114d828d9035cef76cee72bf6b1db
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400289"
---
# <a name="type-of-optional-value-for-optional-parameter-parametername-is-not-cls-compliant"></a><span data-ttu-id="da09c-102">Typ nepovinné hodnoty pro volitelný parametr \<parametername> není kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="da09c-102">Type of optional value for optional parameter \<parametername> is not CLS-compliant</span></span>
<span data-ttu-id="da09c-103">Procedura je označena jako, `<CLSCompliant(True)>` ale deklaruje [nepovinný](../modifiers/optional.md) parametr s výchozí hodnotou nekompatibilního typu.</span><span class="sxs-lookup"><span data-stu-id="da09c-103">A procedure is marked as `<CLSCompliant(True)>` but declares an [Optional](../modifiers/optional.md) parameter with default value of a noncompliant type.</span></span>  
  
 <span data-ttu-id="da09c-104">Aby byl postup kompatibilní s [nezávislostí jazyka a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), musí používat pouze typy kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="da09c-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="da09c-105">To platí pro typy parametrů, návratový typ a typy všech místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="da09c-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span> <span data-ttu-id="da09c-106">Vztahuje se také na výchozí hodnoty nepovinných parametrů.</span><span class="sxs-lookup"><span data-stu-id="da09c-106">It also applies to the default values of optional parameters.</span></span>  
  
 <span data-ttu-id="da09c-107">Následující Visual Basic datové typy nejsou kompatibilní se specifikací CLS:</span><span class="sxs-lookup"><span data-stu-id="da09c-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="da09c-108">SByte – datový typ</span><span class="sxs-lookup"><span data-stu-id="da09c-108">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="da09c-109">UInteger – datový typ</span><span class="sxs-lookup"><span data-stu-id="da09c-109">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="da09c-110">ULong – datový typ</span><span class="sxs-lookup"><span data-stu-id="da09c-110">ULong Data Type</span></span>](../data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="da09c-111">UShort – datový typ</span><span class="sxs-lookup"><span data-stu-id="da09c-111">UShort Data Type</span></span>](../data-types/ushort-data-type.md)  
  
 <span data-ttu-id="da09c-112">Použijete-li <xref:System.CLSCompliantAttribute> atribut na programovací prvek, nastavíte `isCompliant` parametr atributu na hodnotu `True` nebo `False` k označení dodržování předpisů nebo nedodržení předpisů.</span><span class="sxs-lookup"><span data-stu-id="da09c-112">When you apply the <xref:System.CLSCompliantAttribute> attribute to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="da09c-113">Pro tento parametr neexistuje výchozí hodnota a je třeba uvést hodnotu.</span><span class="sxs-lookup"><span data-stu-id="da09c-113">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="da09c-114">Pokud neplatíte <xref:System.CLSCompliantAttribute> pro prvek, je považován za nekompatibilní.</span><span class="sxs-lookup"><span data-stu-id="da09c-114">If you do not apply <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="da09c-115">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="da09c-115">By default, this message is a warning.</span></span> <span data-ttu-id="da09c-116">Informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="da09c-116">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="da09c-117">**ID chyby:** BC40042</span><span class="sxs-lookup"><span data-stu-id="da09c-117">**Error ID:** BC40042</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="da09c-118">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="da09c-118">To correct this error</span></span>  
  
- <span data-ttu-id="da09c-119">Pokud volitelný parametr musí mít výchozí hodnotu tohoto konkrétního typu, odeberte <xref:System.CLSCompliantAttribute> .</span><span class="sxs-lookup"><span data-stu-id="da09c-119">If the optional parameter must have a default value of this particular type, remove <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="da09c-120">Procedura nemůže být kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="da09c-120">The procedure cannot be CLS-compliant.</span></span>  
  
- <span data-ttu-id="da09c-121">Pokud procedura musí být kompatibilní se specifikací CLS, změňte typ této výchozí hodnoty na nejbližší typ kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="da09c-121">If the procedure must be CLS-compliant, change the type of this default value to the closest CLS-compliant type.</span></span> <span data-ttu-id="da09c-122">Například, `UInteger` `Integer` Pokud nepotřebujete rozsah hodnoty nad 2 147 483 647, můžete použít třeba místo.</span><span class="sxs-lookup"><span data-stu-id="da09c-122">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="da09c-123">Pokud budete potřebovat Rozšířený rozsah, můžete nahradit `UInteger` `Long` .</span><span class="sxs-lookup"><span data-stu-id="da09c-123">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="da09c-124">Pokud procházíte s objekty automatizace nebo COM, pamatujte, že některé typy mají odlišnou šířku dat než v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="da09c-124">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="da09c-125">Například `int` obvykle je 16 bitů v jiných prostředích.</span><span class="sxs-lookup"><span data-stu-id="da09c-125">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="da09c-126">Pokud přijímáte 16bitové celé číslo z takové komponenty, deklarujte ho `Short` místo `Integer` ve spravovaném kódu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="da09c-126">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>
