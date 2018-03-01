---
title: "Základní typ &lt;typename&gt; výčtu není kompatibilní se specifikací CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e054f8d992154f66ab1d48a477a7e04900aa5b4d
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="underlying-type-lttypenamegt-of-enum-is-not-cls-compliant"></a><span data-ttu-id="5c0f4-102">Základní typ &lt;typename&gt; výčtu není kompatibilní se specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="5c0f4-102">Underlying type &lt;typename&gt; of Enum is not CLS-compliant</span></span>
<span data-ttu-id="5c0f4-103">Datový typ zadaný pro tento výčet není součástí [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="5c0f4-103">The data type specified for this enumeration is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="5c0f4-104">Toto není chybu v rámci komponenty, protože [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] podporují tento datový typ.</span><span class="sxs-lookup"><span data-stu-id="5c0f4-104">This is not an error within your component, because the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] and [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] support this data type.</span></span> <span data-ttu-id="5c0f4-105">Jiné komponenty, které jsou zapsané ve výhradně kompatibilní se specifikací CLS kódu však nemusí podporovat tento datový typ.</span><span class="sxs-lookup"><span data-stu-id="5c0f4-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="5c0f4-106">Tyto součásti nemusí být možné úspěšně komunikovat s příslušné součásti.</span><span class="sxs-lookup"><span data-stu-id="5c0f4-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="5c0f4-107">Následující [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] datové typy nejsou kompatibilní se specifikací CLS:</span><span class="sxs-lookup"><span data-stu-id="5c0f4-107">The following [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="5c0f4-108">Datový typ SByte</span><span class="sxs-lookup"><span data-stu-id="5c0f4-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="5c0f4-109">Datový typ UInteger</span><span class="sxs-lookup"><span data-stu-id="5c0f4-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="5c0f4-110">Datový typ ULong</span><span class="sxs-lookup"><span data-stu-id="5c0f4-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="5c0f4-111">Datový typ UShort</span><span class="sxs-lookup"><span data-stu-id="5c0f4-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="5c0f4-112">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="5c0f4-112">By default, this message is a warning.</span></span> <span data-ttu-id="5c0f4-113">Další informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5c0f4-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="5c0f4-114">**ID chyby:** BC40032</span><span class="sxs-lookup"><span data-stu-id="5c0f4-114">**Error ID:** BC40032</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5c0f4-115">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="5c0f4-115">To correct this error</span></span>  
  
-   <span data-ttu-id="5c0f4-116">Pokud příslušné součásti rozhraní pouze s jinými [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] součástí, nebo nemá není rozhraní s ostatními součástmi, není potřeba nic nezmění.</span><span class="sxs-lookup"><span data-stu-id="5c0f4-116">If your component interfaces only with other [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="5c0f4-117">Pokud se propojení s nejsou určeny pro součásti [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], je možné určit, buď pomocí reflexe nebo z dokumentace, jestli podporuje tento datový typ.</span><span class="sxs-lookup"><span data-stu-id="5c0f4-117">If you are interfacing with a component not written for the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="5c0f4-118">Pokud ano, není potřeba nic nezmění.</span><span class="sxs-lookup"><span data-stu-id="5c0f4-118">If it does, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="5c0f4-119">Pokud se propojení s komponenty, která nepodporuje tento typ dat, musíte jej nahradit s typem nejbližší kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="5c0f4-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="5c0f4-120">Například v místě z `UInteger` je možné použít `Integer` Pokud nepotřebujete rozsah hodnot výše 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="5c0f4-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="5c0f4-121">Pokud potřebujete rozšířené rozsahu, můžete nahradit `UInteger` s `Long`.</span><span class="sxs-lookup"><span data-stu-id="5c0f4-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="5c0f4-122">Pokud se propojení s objekty automatizace nebo COM, mějte na paměti, že některé typy mají různé datové šířek než [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5c0f4-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="5c0f4-123">Například `uint` je často 16 bitů v jiných prostředích.</span><span class="sxs-lookup"><span data-stu-id="5c0f4-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="5c0f4-124">Argument 16bitové předáte pro tyto součásti, deklarujte ji jako `UShort` místo `UInteger` ve vaší spravované [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kódu.</span><span class="sxs-lookup"><span data-stu-id="5c0f4-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c0f4-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c0f4-125">See Also</span></span>  
 [<span data-ttu-id="5c0f4-126">Reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c0f4-126">Reflection (Visual Basic)</span></span>](../../programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="5c0f4-127">Reflexe</span><span class="sxs-lookup"><span data-stu-id="5c0f4-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
 
