---
title: "Návratový typ funkce & č. 39; &lt;procedurename&gt;& č. 39; není kompatibilní se specifikací CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40027
- vbc40027
helpviewer_keywords:
- BC40027
ms.assetid: 33c088c7-48e7-400c-920e-6d8967e1f3fc
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 866c0001d51a2eff75409c3918a6b6189ca294d8
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="return-type-of-function-39ltprocedurenamegt39-is-not-cls-compliant"></a><span data-ttu-id="90f1e-102">Návratový typ funkce & č. 39; &lt;procedurename&gt;& č. 39; není kompatibilní se specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="90f1e-102">Return type of function &#39;&lt;procedurename&gt;&#39; is not CLS-compliant</span></span>
<span data-ttu-id="90f1e-103">A `Function` postup je označena jako `<CLSCompliant(True)>` , ale vrací typ, který je označen jako `<CLSCompliant(False)>`, není označena nebo nelze vyřešit, protože je typu nesplňujících požadavky.</span><span class="sxs-lookup"><span data-stu-id="90f1e-103">A `Function` procedure is marked as `<CLSCompliant(True)>` but returns a type that is marked as `<CLSCompliant(False)>`, is not marked, or does not qualify because it is a noncompliant type.</span></span>  
  
 <span data-ttu-id="90f1e-104">Pro proceduru splňovat [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS), musí používat pouze typy kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="90f1e-104">For a procedure to be compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), it must use only CLS-compliant types.</span></span> <span data-ttu-id="90f1e-105">To platí pro typy parametrů, návratový typ a typy všechny místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="90f1e-105">This applies to the types of the parameters, the return type, and the types of all its local variables.</span></span>  
  
 <span data-ttu-id="90f1e-106">Následující [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] datové typy nejsou kompatibilní se specifikací CLS:</span><span class="sxs-lookup"><span data-stu-id="90f1e-106">The following [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="90f1e-107">Datový typ SByte</span><span class="sxs-lookup"><span data-stu-id="90f1e-107">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="90f1e-108">Datový typ UInteger</span><span class="sxs-lookup"><span data-stu-id="90f1e-108">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="90f1e-109">Datový typ ULong</span><span class="sxs-lookup"><span data-stu-id="90f1e-109">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="90f1e-110">Datový typ UShort</span><span class="sxs-lookup"><span data-stu-id="90f1e-110">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="90f1e-111">Pokud použijete <xref:System.CLSCompliantAttribute> programovací element, nastavíte atributu `isCompliant` buď parametr `True` nebo `False` indikující dodržování předpisů nebo nesplňujících požadavky.</span><span class="sxs-lookup"><span data-stu-id="90f1e-111">When you apply the <xref:System.CLSCompliantAttribute> to a programming element, you set the attribute's `isCompliant` parameter to either `True` or `False` to indicate compliance or noncompliance.</span></span> <span data-ttu-id="90f1e-112">Neexistuje žádný výchozí hodnotou tohoto parametru, a je nutné zadat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="90f1e-112">There is no default for this parameter, and you must supply a value.</span></span>  
  
 <span data-ttu-id="90f1e-113">Pokud se nevztahují <xref:System.CLSCompliantAttribute> na element, je považován za nedodržuje předpisy.</span><span class="sxs-lookup"><span data-stu-id="90f1e-113">If you do not apply the <xref:System.CLSCompliantAttribute> to an element, it is considered to be noncompliant.</span></span>  
  
 <span data-ttu-id="90f1e-114">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="90f1e-114">By default, this message is a warning.</span></span> <span data-ttu-id="90f1e-115">Informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="90f1e-115">For information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="90f1e-116">**ID chyby:** BC40027</span><span class="sxs-lookup"><span data-stu-id="90f1e-116">**Error ID:** BC40027</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="90f1e-117">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="90f1e-117">To correct this error</span></span>  
  
-   <span data-ttu-id="90f1e-118">Pokud `Function` postupu musí vrátit tento konkrétní typ, odeberte <xref:System.CLSCompliantAttribute>.</span><span class="sxs-lookup"><span data-stu-id="90f1e-118">If the `Function` procedure must return this particular type, remove the <xref:System.CLSCompliantAttribute>.</span></span> <span data-ttu-id="90f1e-119">Postup nemůže být kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="90f1e-119">The procedure cannot be CLS-compliant.</span></span>  
  
-   <span data-ttu-id="90f1e-120">Pokud `Function` postupu musí být kompatibilní se specifikací CLS, změnit návratový typ na nejbližší typ kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="90f1e-120">If the `Function` procedure must be CLS-compliant, change the return type to the closest CLS-compliant type.</span></span> <span data-ttu-id="90f1e-121">Například v místě z `UInteger` je možné použít `Integer` Pokud nepotřebujete rozsah hodnot výše 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="90f1e-121">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="90f1e-122">Pokud potřebujete rozšířené rozsahu, můžete nahradit `UInteger` s `Long`.</span><span class="sxs-lookup"><span data-stu-id="90f1e-122">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="90f1e-123">Pokud se propojení s objekty automatizace nebo COM, mějte na paměti, že některé typy mají různé datové šířek než [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="90f1e-123">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="90f1e-124">Například `int` je často 16 bitů v jiných prostředích.</span><span class="sxs-lookup"><span data-stu-id="90f1e-124">For example, `int` is often 16 bits in other environments.</span></span> <span data-ttu-id="90f1e-125">Pokud k takové součásti jsou vrácení 16bitové celé číslo, deklarujte ji jako `Short` místo `Integer` ve vaší spravované [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kódu.</span><span class="sxs-lookup"><span data-stu-id="90f1e-125">If you are returning a 16-bit integer to such a component, declare it as `Short` instead of `Integer` in your managed [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code.</span></span>