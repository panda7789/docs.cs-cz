---
title: Návratový typ funkce &#39; &lt;název_procedury&gt; &#39; není kompatibilní se Specifikací CLS
ms.date: 07/20/2015
f1_keywords:
- bc40027
- vbc40027
helpviewer_keywords:
- BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
ms.openlocfilehash: b7704ee63031c38f708a2243e84b880c25fcf819
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39243778"
---
# <a name="return-type-of-function-39ltprocedurenamegt39-is-not-cls-compliant"></a><span data-ttu-id="67742-102">Návratový typ funkce &#39; &lt;název_procedury&gt; &#39; není kompatibilní se Specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="67742-102">Return type of function &#39;&lt;procedurename&gt;&#39; is not CLS-compliant</span></span>
<span data-ttu-id="67742-103">A `Function` postup je označen jako `<CLSCompliant(True)>` , ale vrací typ, který je označen jako `<CLSCompliant(False)>`, není označena nebo nesplňuje, protože se jedná o nekompatibilní typ.</span><span class="sxs-lookup"><span data-stu-id="67742-103">A `Function` procedure is marked as `<CLSCompliant(True)>` but returns a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="67742-104">Postup, který má být zajištěn soulad [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), musí používat jenom typy kompatibilní se Specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="67742-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="67742-105">To platí pro typy parametrů, návratový typ a typy všech místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="67742-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="67742-106">Následující datové typy jazyka Visual Basic nejsou kompatibilní se Specifikací CLS:</span><span class="sxs-lookup"><span data-stu-id="67742-106">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="67742-107">Datový typ SByte</span><span class="sxs-lookup"><span data-stu-id="67742-107">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="67742-108">Datový typ UInteger</span><span class="sxs-lookup"><span data-stu-id="67742-108">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="67742-109">Datový typ ULong</span><span class="sxs-lookup"><span data-stu-id="67742-109">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="67742-110">Datový typ UShort</span><span class="sxs-lookup"><span data-stu-id="67742-110">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="67742-111">Pokud použijete <xref:System.CLSCompliantAttribute> na programovací prvek, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` k označení dodržování předpisů nebo při nedodržení předpisů.</span><span class="sxs-lookup"><span data-stu-id="67742-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="67742-112">Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="67742-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="67742-113">Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, se považuje za jako nevyhovující.</span><span class="sxs-lookup"><span data-stu-id="67742-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="67742-114">Ve výchozím nastavení tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="67742-114">By default, this message is a warning.</span></span> <span data-ttu-id="67742-115">Informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="67742-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="67742-116">**ID chyby:** BC40027</span><span class="sxs-lookup"><span data-stu-id="67742-116">**Error ID:** BC40027</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="67742-117">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="67742-117">To correct this error</span></span>  
  
-   <span data-ttu-id="67742-118">Pokud `Function` procedury musí vrátit tento konkrétní typ, odeberte <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="67742-118">If the `Function` procedure must return this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="67742-119">Procedura nemůže být kompatibilní se Specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="67742-119">The procedure cannot be CLS-compliant.</span></span>  
  
-   <span data-ttu-id="67742-120">Pokud `Function` postupu musí být kompatibilní se Specifikací CLS, změňte návratový typ na nejbližší typ. kompatibilní se Specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="67742-120">If the `Function` procedure must be CLS-compliant, change the return type to the closest CLS-compliant type.</span></span> <span data-ttu-id="67742-121">Například místo hodnoty `UInteger` je možné použít `Integer` Pokud nepotřebujete rozsah hodnot nad 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="67742-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="67742-122">Pokud budete potřebovat delší rozsah, můžete nahradit `UInteger` s `Long`.</span><span class="sxs-lookup"><span data-stu-id="67742-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="67742-123">Při vzájemném propojování s objekty automatizace nebo COM, mějte na paměti, že některé typy mají různou šířkou dat než [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="67742-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="67742-124">Například `int` je často 16 bitů v jiných prostředích.</span><span class="sxs-lookup"><span data-stu-id="67742-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="67742-125">Pokud se vrací 16bitové celé číslo takové součásti, deklarujte ho jako `Short` místo `Integer` v spravovaného kódu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="67742-125">If you are returning a 16-bit integer to such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>