---
title: "Typ volitelné hodnoty pro volitelný parametr &lt;parametername&gt; není kompatibilní se specifikací CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords: BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 442ff2e4b582287e03f425dad98128726fe18c43
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="type-of-optional-value-for-optional-parameter-ltparameternamegt-is-not-cls-compliant"></a><span data-ttu-id="908de-102">Typ volitelné hodnoty pro volitelný parametr &lt;parametername&gt; není kompatibilní se specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="908de-102">Type of optional value for optional parameter &lt;parametername&gt; is not CLS-compliant</span></span>
<span data-ttu-id="908de-103">Postup je označena jako `<CLSCompliant(True)>` deklaruje, ale [volitelné](../../../visual-basic/language-reference/modifiers/optional.md) parametr s hodnotou výchozí nekompatibilních typu.</span><span class="sxs-lookup"><span data-stu-id="908de-103">A procedure is marked as `<CLSCompliant(True)>` but declares an [Optional](../../../visual-basic/language-reference/modifiers/optional.md) parameter with default value of a noncompliant type.</span></span>  
  
 <span data-ttu-id="908de-104">Pro proceduru splňovat [jazyková nezávislost a jazykově nezávislé komponenty](https://msdn.microsoft.com/library/12a7a7h3) (CLS), musí používat pouze typy kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="908de-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="908de-105">To platí pro typy parametrů, návratový typ a typy všechny místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="908de-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span> <span data-ttu-id="908de-106">Platí také pro výchozí hodnoty volitelné parametry.</span><span class="sxs-lookup"><span data-stu-id="908de-106">It also applies to the default values of optional parameters.</span></span>  
  
 <span data-ttu-id="908de-107">Následující [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] datové typy nejsou kompatibilní se specifikací CLS:</span><span class="sxs-lookup"><span data-stu-id="908de-107">The following [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="908de-108">SByte – datový typ</span><span class="sxs-lookup"><span data-stu-id="908de-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="908de-109">Uinteger – datový typ</span><span class="sxs-lookup"><span data-stu-id="908de-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="908de-110">Ulong – datový typ</span><span class="sxs-lookup"><span data-stu-id="908de-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="908de-111">Ushort – datový typ</span><span class="sxs-lookup"><span data-stu-id="908de-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="908de-112">Pokud použijete <xref:System.CLSCompliantAttribute> atribut programovací element, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` indikující dodržování předpisů nebo nesplňujících požadavky.</span><span class="sxs-lookup"><span data-stu-id="908de-112">When you apply the <xref:System.CLSCompliantAttribute> attribute to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="908de-113">Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="908de-113">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="908de-114">Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, je považován za nedodržuje předpisy.</span><span class="sxs-lookup"><span data-stu-id="908de-114">If you do not apply <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="908de-115">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="908de-115">By default, this message is a warning.</span></span> <span data-ttu-id="908de-116">Informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="908de-116">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="908de-117">**ID chyby:** BC40042</span><span class="sxs-lookup"><span data-stu-id="908de-117">**Error ID:** BC40042</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="908de-118">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="908de-118">To correct this error</span></span>  
  
-   <span data-ttu-id="908de-119">Pokud volitelný parametr musí mít výchozí hodnotu tohoto konkrétního typu, odeberte <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="908de-119">If the optional parameter must have a default value of this particular type, remove <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="908de-120">Postup nemůže být kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="908de-120">The procedure cannot be CLS-compliant.</span></span>  
  
-   <span data-ttu-id="908de-121">Pokud postup musí být kompatibilní se specifikací CLS, změňte typ této výchozí hodnoty na typ nejbližší kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="908de-121">If the procedure must be CLS-compliant, change the type of this default value to the closest CLS-compliant type.</span></span> <span data-ttu-id="908de-122">Například v místě z `UInteger` je možné použít `Integer` Pokud nepotřebujete rozsah hodnot výše 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="908de-122">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="908de-123">Pokud potřebujete rozšířené rozsahu, můžete nahradit `UInteger` s `Long`.</span><span class="sxs-lookup"><span data-stu-id="908de-123">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="908de-124">Pokud se propojení s objekty automatizace nebo COM, mějte na paměti, že některé typy mají různé datové šířek než [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="908de-124">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="908de-125">Například `int` je často 16 bitů v jiných prostředích.</span><span class="sxs-lookup"><span data-stu-id="908de-125">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="908de-126">Pokud je přijímáte 16bitové celé číslo z těchto součástí, deklarujte ji jako `Short` místo `Integer` ve vaší spravované [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kódu.</span><span class="sxs-lookup"><span data-stu-id="908de-126">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="908de-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="908de-127">See Also</span></span>  
 [<span data-ttu-id="908de-128">\<PAVE přes > zápis kompatibilní se specifikací CLS kódu</span><span class="sxs-lookup"><span data-stu-id="908de-128">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
