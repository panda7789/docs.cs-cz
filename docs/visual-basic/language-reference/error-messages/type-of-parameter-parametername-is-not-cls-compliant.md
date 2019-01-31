---
title: Typ parametru '<parametername>' není kompatibilní se specifikací CLS.
ms.date: 07/20/2015
f1_keywords:
- vbc40028
- bc40028
helpviewer_keywords:
- BC40028
ms.assetid: dfa1f6f9-bb88-44ad-b85f-149144363d41
ms.openlocfilehash: e0852536a86dd415334f95a47ceb800ed2c591ad
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55265919"
---
# <a name="type-of-parameter-parametername-is-not-cls-compliant"></a><span data-ttu-id="15904-102">Typ parametru '\<parametername >' není kompatibilní se Specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="15904-102">Type of parameter '\<parametername>' is not CLS-compliant</span></span>
<span data-ttu-id="15904-103">Postup je označen jako `<CLSCompliant(True)>` ale deklaruje parametr s typem, který je označen jako `<CLSCompliant(False)>`, není označena nebo nesplňuje, protože se jedná o nekompatibilní typ.</span><span class="sxs-lookup"><span data-stu-id="15904-103">A procedure is marked as `<CLSCompliant(True)>` but declares a parameter with a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="15904-104">Postup, který má být zajištěn soulad [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), musí používat jenom typy kompatibilní se Specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="15904-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="15904-105">To platí pro typy parametrů, návratový typ a typy všech místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="15904-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="15904-106">Následující datové typy jazyka Visual Basic nejsou kompatibilní se Specifikací CLS:</span><span class="sxs-lookup"><span data-stu-id="15904-106">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="15904-107">Datový typ SByte</span><span class="sxs-lookup"><span data-stu-id="15904-107">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="15904-108">Datový typ UInteger</span><span class="sxs-lookup"><span data-stu-id="15904-108">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="15904-109">Datový typ ULong</span><span class="sxs-lookup"><span data-stu-id="15904-109">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="15904-110">Datový typ UShort</span><span class="sxs-lookup"><span data-stu-id="15904-110">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="15904-111">Pokud použijete <xref:System.CLSCompliantAttribute> na programovací prvek, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` k označení dodržování předpisů nebo při nedodržení předpisů.</span><span class="sxs-lookup"><span data-stu-id="15904-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="15904-112">Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="15904-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="15904-113">Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, se považuje za jako nevyhovující.</span><span class="sxs-lookup"><span data-stu-id="15904-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="15904-114">Ve výchozím nastavení tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="15904-114">By default, this message is a warning.</span></span> <span data-ttu-id="15904-115">Informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="15904-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="15904-116">**ID chyby:** BC40028</span><span class="sxs-lookup"><span data-stu-id="15904-116">**Error ID:** BC40028</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="15904-117">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="15904-117">To correct this error</span></span>  
  
-   <span data-ttu-id="15904-118">Pokud proces musí přijmout parametr tohoto konkrétního typu, odeberte <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="15904-118">If the procedure must take a parameter of this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="15904-119">Procedura nemůže být kompatibilní se Specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="15904-119">The procedure cannot be CLS-compliant.</span></span>  
  
-   <span data-ttu-id="15904-120">Pokud procedura musí být kompatibilní se Specifikací CLS, změňte typ tohoto parametru na nejbližší typ. kompatibilní se Specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="15904-120">If the procedure must be CLS-compliant, change the type of this parameter to the closest CLS-compliant type.</span></span> <span data-ttu-id="15904-121">Například místo hodnoty `UInteger` je možné použít `Integer` Pokud nepotřebujete rozsah hodnot nad 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="15904-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="15904-122">Pokud budete potřebovat delší rozsah, můžete nahradit `UInteger` s `Long`.</span><span class="sxs-lookup"><span data-stu-id="15904-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="15904-123">Při vzájemném propojování s objekty automatizace nebo COM, mějte na paměti, že některé typy mají různou šířkou dat než [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="15904-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="15904-124">Například `int` je často 16 bitů v jiných prostředích.</span><span class="sxs-lookup"><span data-stu-id="15904-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="15904-125">Pokud přijímáte 16bitové celé číslo z takové součásti, deklarujte ho jako `Short` místo `Integer` v spravovaného kódu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="15904-125">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>