---
title: Typ nepovinné hodnoty pro volitelný parametr <parametername> není kompatibilní se specifikací CLS.
ms.date: 07/20/2015
f1_keywords:
- BC40042
- vbc40042
helpviewer_keywords:
- BC40042
ms.assetid: 1d6eae29-4ad3-4434-bde4-a53b6051adf5
ms.openlocfilehash: ee7d208f7a579f81690ffbda265bde29316e4ec3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664306"
---
# <a name="type-of-optional-value-for-optional-parameter-parametername-is-not-cls-compliant"></a><span data-ttu-id="8d824-102">Typ nepovinné hodnoty pro nepovinný parametr \<parametername > není kompatibilní se Specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="8d824-102">Type of optional value for optional parameter \<parametername> is not CLS-compliant</span></span>
<span data-ttu-id="8d824-103">Postup je označen jako `<CLSCompliant(True)>` deklaruje, ale [volitelné](../../../visual-basic/language-reference/modifiers/optional.md) parametr s výchozí hodnotou typu nedodržující předpisy.</span><span class="sxs-lookup"><span data-stu-id="8d824-103">A procedure is marked as `<CLSCompliant(True)>` but declares an [Optional](../../../visual-basic/language-reference/modifiers/optional.md) parameter with default value of a noncompliant type.</span></span>  
  
 <span data-ttu-id="8d824-104">Postup, který má být zajištěn soulad [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), musí používat jenom typy kompatibilní se Specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="8d824-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="8d824-105">To platí pro typy parametrů, návratový typ a typy všech místních proměnných.</span><span class="sxs-lookup"><span data-stu-id="8d824-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span> <span data-ttu-id="8d824-106">Platí také pro výchozími hodnotami nepovinných parametrů.</span><span class="sxs-lookup"><span data-stu-id="8d824-106">It also applies to the default values of optional parameters.</span></span>  
  
 <span data-ttu-id="8d824-107">Následující datové typy jazyka Visual Basic nejsou kompatibilní se Specifikací CLS:</span><span class="sxs-lookup"><span data-stu-id="8d824-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="8d824-108">Datový typ SByte</span><span class="sxs-lookup"><span data-stu-id="8d824-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="8d824-109">Datový typ UInteger</span><span class="sxs-lookup"><span data-stu-id="8d824-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="8d824-110">Datový typ ULong</span><span class="sxs-lookup"><span data-stu-id="8d824-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="8d824-111">Datový typ UShort</span><span class="sxs-lookup"><span data-stu-id="8d824-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="8d824-112">Pokud použijete <xref:System.CLSCompliantAttribute> atribut na programovací prvek, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` k označení dodržování předpisů nebo při nedodržení předpisů.</span><span class="sxs-lookup"><span data-stu-id="8d824-112">When you apply the <xref:System.CLSCompliantAttribute> attribute to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="8d824-113">Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8d824-113">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="8d824-114">Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, se považuje za jako nevyhovující.</span><span class="sxs-lookup"><span data-stu-id="8d824-114">If you do not apply <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="8d824-115">Ve výchozím nastavení tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="8d824-115">By default, this message is a warning.</span></span> <span data-ttu-id="8d824-116">Informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="8d824-116">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="8d824-117">**ID chyby:** BC40042</span><span class="sxs-lookup"><span data-stu-id="8d824-117">**Error ID:** BC40042</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8d824-118">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="8d824-118">To correct this error</span></span>  
  
- <span data-ttu-id="8d824-119">Pokud volitelný parametr musí mít výchozí hodnotu tohoto konkrétního typu, odeberte <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8d824-119">If the optional parameter must have a default value of this particular type, remove <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="8d824-120">Procedura nemůže být kompatibilní se Specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="8d824-120">The procedure cannot be CLS-compliant.</span></span>  
  
- <span data-ttu-id="8d824-121">Pokud procedura musí být kompatibilní se Specifikací CLS, změňte typ tuto výchozí hodnotu na nejbližší typ. kompatibilní se Specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="8d824-121">If the procedure must be CLS-compliant, change the type of this default value to the closest CLS-compliant type.</span></span> <span data-ttu-id="8d824-122">Například místo hodnoty `UInteger` je možné použít `Integer` Pokud nepotřebujete rozsah hodnot nad 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="8d824-122">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="8d824-123">Pokud budete potřebovat delší rozsah, můžete nahradit `UInteger` s `Long`.</span><span class="sxs-lookup"><span data-stu-id="8d824-123">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="8d824-124">Při vzájemném propojování s objekty automatizace nebo COM, mějte na paměti, že některé typy mají různou šířkou dat než [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8d824-124">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="8d824-125">Například `int` je často 16 bitů v jiných prostředích.</span><span class="sxs-lookup"><span data-stu-id="8d824-125">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="8d824-126">Pokud přijímáte 16bitové celé číslo z takové součásti, deklarujte ho jako `Short` místo `Integer` v spravovaného kódu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8d824-126">If you are accepting a 16-bit integer from such a component, declare it as `Short` instead of `Integer` in your managed Visual Basic code.</span></span>