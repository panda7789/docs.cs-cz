---
title: Základní typ &lt;typename&gt; výčtu není kompatibilní se specifikací CLS
ms.date: 07/20/2015
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
ms.openlocfilehash: 876a59d1441c1ba4c5057556d5ef2fb2ecb43af6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33596616"
---
# <a name="underlying-type-lttypenamegt-of-enum-is-not-cls-compliant"></a><span data-ttu-id="01876-102">Základní typ &lt;typename&gt; výčtu není kompatibilní se specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="01876-102">Underlying type &lt;typename&gt; of Enum is not CLS-compliant</span></span>
<span data-ttu-id="01876-103">Datový typ zadaný pro tento výčet není součástí [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="01876-103">The data type specified for this enumeration is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="01876-104">Toto není chybu v rámci komponenty, protože [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] a tento typ dat jazyka Visual Basic podporován.</span><span class="sxs-lookup"><span data-stu-id="01876-104">This is not an error within your component, because the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] and Visual Basic support this data type.</span></span> <span data-ttu-id="01876-105">Jiné komponenty, které jsou zapsané ve výhradně kompatibilní se specifikací CLS kódu však nemusí podporovat tento datový typ.</span><span class="sxs-lookup"><span data-stu-id="01876-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="01876-106">Tyto součásti nemusí být možné úspěšně komunikovat s příslušné součásti.</span><span class="sxs-lookup"><span data-stu-id="01876-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="01876-107">Následující typy dat jazyka Visual Basic nejsou kompatibilní se specifikací CLS:</span><span class="sxs-lookup"><span data-stu-id="01876-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="01876-108">Datový typ SByte</span><span class="sxs-lookup"><span data-stu-id="01876-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="01876-109">Datový typ UInteger</span><span class="sxs-lookup"><span data-stu-id="01876-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="01876-110">Datový typ ULong</span><span class="sxs-lookup"><span data-stu-id="01876-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="01876-111">Datový typ UShort</span><span class="sxs-lookup"><span data-stu-id="01876-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="01876-112">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="01876-112">By default, this message is a warning.</span></span> <span data-ttu-id="01876-113">Další informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="01876-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="01876-114">**ID chyby:** BC40032</span><span class="sxs-lookup"><span data-stu-id="01876-114">**Error ID:** BC40032</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="01876-115">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="01876-115">To correct this error</span></span>  
  
-   <span data-ttu-id="01876-116">Pokud příslušné součásti rozhraní pouze s jinými [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] součástí, nebo nemá není rozhraní s ostatními součástmi, není potřeba nic nezmění.</span><span class="sxs-lookup"><span data-stu-id="01876-116">If your component interfaces only with other [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="01876-117">Pokud se propojení s nejsou určeny pro součásti [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], je možné určit, buď pomocí reflexe nebo z dokumentace, jestli podporuje tento datový typ.</span><span class="sxs-lookup"><span data-stu-id="01876-117">If you are interfacing with a component not written for the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="01876-118">Pokud ano, není potřeba nic nezmění.</span><span class="sxs-lookup"><span data-stu-id="01876-118">If it does, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="01876-119">Pokud se propojení s komponenty, která nepodporuje tento typ dat, musíte jej nahradit s typem nejbližší kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="01876-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="01876-120">Například v místě z `UInteger` je možné použít `Integer` Pokud nepotřebujete rozsah hodnot výše 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="01876-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="01876-121">Pokud potřebujete rozšířené rozsahu, můžete nahradit `UInteger` s `Long`.</span><span class="sxs-lookup"><span data-stu-id="01876-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="01876-122">Pokud se propojení s objekty automatizace nebo COM, mějte na paměti, že některé typy mají různé datové šířek než [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="01876-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="01876-123">Například `uint` je často 16 bitů v jiných prostředích.</span><span class="sxs-lookup"><span data-stu-id="01876-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="01876-124">Argument 16bitové předáte pro tyto součásti, deklarujte ji jako `UShort` místo `UInteger` v spravovaného kódu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="01876-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01876-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="01876-125">See Also</span></span>  
 [<span data-ttu-id="01876-126">Reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="01876-126">Reflection (Visual Basic)</span></span>](../../programming-guide/concepts/reflection.md)  
 [<span data-ttu-id="01876-127">Reflexe</span><span class="sxs-lookup"><span data-stu-id="01876-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
 
