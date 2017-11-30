---
title: "Typ parametru & č. 39; &lt;parametername&gt;& č. 39; není kompatibilní se specifikací CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40028
- bc40028
helpviewer_keywords: BC40028
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1c495a21603f1977bd0f0630104f75ab02728928
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="type-of-parameter-39ltparameternamegt39-is-not-cls-compliant"></a><span data-ttu-id="c5867-102">Typ parametru & č. 39; &lt;parametername&gt;& č. 39; není kompatibilní se specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="c5867-102">Type of parameter &#39;&lt;parametername&gt;&#39; is not CLS-compliant</span></span>
<span data-ttu-id="c5867-103">Postup je označena jako `<CLSCompliant(True)>` ale deklaruje parametr s typem, který je označený jako `<CLSCompliant(False)>`, není označena nebo nelze vyřešit, protože je typu nesplňujících požadavky.</span><span class="sxs-lookup"><span data-stu-id="c5867-103">A procedure is marked as `<CLSCompliant(True)>` but declares a parameter with a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="c5867-104">Pro proceduru splňovat [jazyková nezávislost a jazykově nezávislé komponenty](https://msdn.microsoft.com/library/12a7a7h3) (CLS), musí používat pouze typy kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="c5867-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="c5867-105">To platí pro typy parametrů, návratový typ a typy všechny místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="c5867-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="c5867-106">Následující [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] datové typy nejsou kompatibilní se specifikací CLS:</span><span class="sxs-lookup"><span data-stu-id="c5867-106">The following [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="c5867-107">SByte – datový typ</span><span class="sxs-lookup"><span data-stu-id="c5867-107">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="c5867-108">Uinteger – datový typ</span><span class="sxs-lookup"><span data-stu-id="c5867-108">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="c5867-109">Ulong – datový typ</span><span class="sxs-lookup"><span data-stu-id="c5867-109">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="c5867-110">Ushort – datový typ</span><span class="sxs-lookup"><span data-stu-id="c5867-110">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="c5867-111">Pokud použijete <xref:System.CLSCompliantAttribute> programovací element, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` indikující dodržování předpisů nebo nesplňujících požadavky.</span><span class="sxs-lookup"><span data-stu-id="c5867-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="c5867-112">Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c5867-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="c5867-113">Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, je považován za nedodržuje předpisy.</span><span class="sxs-lookup"><span data-stu-id="c5867-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="c5867-114">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="c5867-114">By default, this message is a warning.</span></span> <span data-ttu-id="c5867-115">Informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c5867-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="c5867-116">**ID chyby:** BC40028</span><span class="sxs-lookup"><span data-stu-id="c5867-116">**Error ID:** BC40028</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c5867-117">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="c5867-117">To correct this error</span></span>  
  
-   <span data-ttu-id="c5867-118">Pokud postup vyžaduje parametr tohoto konkrétního typu, odeberte <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c5867-118">If the procedure must take a parameter of this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="c5867-119">Postup nemůže být kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="c5867-119">The procedure cannot be CLS-compliant.</span></span>  
  
-   <span data-ttu-id="c5867-120">Pokud postup musí být kompatibilní se specifikací CLS, změňte typ tohoto parametru na typ nejbližší kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="c5867-120">If the procedure must be CLS-compliant, change the type of this parameter to the closest CLS-compliant type.</span></span> <span data-ttu-id="c5867-121">Například v místě z `UInteger` je možné použít `Integer` Pokud nepotřebujete rozsah hodnot výše 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="c5867-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="c5867-122">Pokud potřebujete rozšířené rozsahu, můžete nahradit `UInteger` s `Long`.</span><span class="sxs-lookup"><span data-stu-id="c5867-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="c5867-123">Pokud se propojení s objekty automatizace nebo COM, mějte na paměti, že některé typy mají různé datové šířek než [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c5867-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="c5867-124">Například `int` je často 16 bitů v jiných prostředích.</span><span class="sxs-lookup"><span data-stu-id="c5867-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="c5867-125">Pokud je přijímáte 16bitové celé číslo z těchto součástí, deklarujte ji jako `Short` místo `Integer` ve vaší spravované [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kódu.</span><span class="sxs-lookup"><span data-stu-id="c5867-125">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5867-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5867-126">See Also</span></span>  
 [<span data-ttu-id="c5867-127">\<PAVE přes > zápis kompatibilní se specifikací CLS kódu</span><span class="sxs-lookup"><span data-stu-id="c5867-127">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
