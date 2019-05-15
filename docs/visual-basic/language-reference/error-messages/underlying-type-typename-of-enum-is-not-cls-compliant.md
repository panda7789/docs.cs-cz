---
title: Základní typ <typename> Enum není kompatibilní se specifikací CLS.
ms.date: 07/20/2015
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
ms.openlocfilehash: 7d4566637da74726867c55ddf89b965d055e5d14
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589930"
---
# <a name="underlying-type-typename-of-enum-is-not-cls-compliant"></a><span data-ttu-id="00b53-102">Základní typ \<typename > Enum není kompatibilní se Specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="00b53-102">Underlying type \<typename> of Enum is not CLS-compliant</span></span>
<span data-ttu-id="00b53-103">Datový typ zadaný pro tento výčet není součástí [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="00b53-103">The data type specified for this enumeration is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="00b53-104">Nejedná se k chybě v komponentě, protože tento typ dat nepodporuje rozhraní .NET Framework a jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="00b53-104">This is not an error within your component, because the .NET Framework and Visual Basic support this data type.</span></span> <span data-ttu-id="00b53-105">Jiné součásti, které jsou napsané v striktně kompatibilní se Specifikací CLS kódu však nemusí podporovat tento typ dat.</span><span class="sxs-lookup"><span data-stu-id="00b53-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="00b53-106">Takové součásti nemusí být úspěšně komunikovat s vaší komponentě.</span><span class="sxs-lookup"><span data-stu-id="00b53-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="00b53-107">Následující datové typy jazyka Visual Basic nejsou kompatibilní se Specifikací CLS:</span><span class="sxs-lookup"><span data-stu-id="00b53-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="00b53-108">Datový typ SByte</span><span class="sxs-lookup"><span data-stu-id="00b53-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="00b53-109">Datový typ UInteger</span><span class="sxs-lookup"><span data-stu-id="00b53-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="00b53-110">Datový typ ULong</span><span class="sxs-lookup"><span data-stu-id="00b53-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="00b53-111">Datový typ UShort</span><span class="sxs-lookup"><span data-stu-id="00b53-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="00b53-112">Ve výchozím nastavení tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="00b53-112">By default, this message is a warning.</span></span> <span data-ttu-id="00b53-113">Další informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="00b53-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="00b53-114">**ID chyby:** BC40032</span><span class="sxs-lookup"><span data-stu-id="00b53-114">**Error ID:** BC40032</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="00b53-115">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="00b53-115">To correct this error</span></span>  
  
- <span data-ttu-id="00b53-116">Pokud vaše komponenta rozhraní pouze s jinými součástmi rozhraní .NET Framework, nebo není rozhraní s ostatními součástmi, není potřeba nic měnit.</span><span class="sxs-lookup"><span data-stu-id="00b53-116">If your component interfaces only with other .NET Framework components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
- <span data-ttu-id="00b53-117">Při vzájemném propojování součástí, které nejsou napsané pro rozhraní .NET Framework, je možné prostřednictvím reflexe nebo dokumentaci ke službě, určit, jestli je tento typ dat podporuje.</span><span class="sxs-lookup"><span data-stu-id="00b53-117">If you are interfacing with a component not written for the .NET Framework, you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="00b53-118">Pokud ano, není potřeba nic měnit.</span><span class="sxs-lookup"><span data-stu-id="00b53-118">If it does, you do not need to change anything.</span></span>  
  
- <span data-ttu-id="00b53-119">Při vzájemném propojování součástí, která nepodporuje tento typ dat, musíte jej nahradit s typem nejbližší kompatibilní se Specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="00b53-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="00b53-120">Například místo hodnoty `UInteger` je možné použít `Integer` Pokud nepotřebujete rozsah hodnot nad 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="00b53-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="00b53-121">Pokud budete potřebovat delší rozsah, můžete nahradit `UInteger` s `Long`.</span><span class="sxs-lookup"><span data-stu-id="00b53-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="00b53-122">Při vzájemném propojování s objekty automatizace nebo COM, mějte na paměti, že některé typy mají různou šířkou dat než v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="00b53-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="00b53-123">Například `uint` je často 16 bitů v jiných prostředích.</span><span class="sxs-lookup"><span data-stu-id="00b53-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="00b53-124">Pokud takové součásti předáváte 16bitový argument, deklarujte ho jako `UShort` místo `UInteger` v spravovaného kódu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="00b53-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00b53-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="00b53-125">See also</span></span>

- [<span data-ttu-id="00b53-126">Reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00b53-126">Reflection (Visual Basic)</span></span>](../../programming-guide/concepts/reflection.md)
- [<span data-ttu-id="00b53-127">Reflexe</span><span class="sxs-lookup"><span data-stu-id="00b53-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
