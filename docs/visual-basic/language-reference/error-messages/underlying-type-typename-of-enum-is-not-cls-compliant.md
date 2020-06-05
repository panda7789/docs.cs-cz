---
title: Základní typ <typename> Enum není kompatibilní se specifikací CLS.
ms.date: 07/20/2015
f1_keywords:
- vbc40032
- bc40032
helpviewer_keywords:
- BC40032
ms.assetid: 32bf1949-fd73-456c-a323-bf1ffe1320ed
ms.openlocfilehash: 79faf0038b2b313bdc21e12c8ae76854bcd6957f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406570"
---
# <a name="underlying-type-typename-of-enum-is-not-cls-compliant"></a><span data-ttu-id="5d5e2-102">Základní typ \<typename> Enum není kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="5d5e2-102">Underlying type \<typename> of Enum is not CLS-compliant</span></span>
<span data-ttu-id="5d5e2-103">Datový typ zadaný pro tento výčet není součástí [nezávislého jazyka a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="5d5e2-103">The data type specified for this enumeration is not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="5d5e2-104">Nejedná se o chybu v rámci vaší komponenty, protože .NET Framework a Visual Basic podporují tento datový typ.</span><span class="sxs-lookup"><span data-stu-id="5d5e2-104">This is not an error within your component, because the .NET Framework and Visual Basic support this data type.</span></span> <span data-ttu-id="5d5e2-105">Nicméně jiná komponenta napsaná v striktně kódu kompatibilním se specifikací CLS nemusí tento datový typ podporovat.</span><span class="sxs-lookup"><span data-stu-id="5d5e2-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="5d5e2-106">Taková součást nemusí být schopná úspěšně pracovat s vaší komponentou.</span><span class="sxs-lookup"><span data-stu-id="5d5e2-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="5d5e2-107">Následující Visual Basic datové typy nejsou kompatibilní se specifikací CLS:</span><span class="sxs-lookup"><span data-stu-id="5d5e2-107">The following Visual Basic data types are not CLS-compliant:</span></span>  
  
- [<span data-ttu-id="5d5e2-108">SByte – datový typ</span><span class="sxs-lookup"><span data-stu-id="5d5e2-108">SByte Data Type</span></span>](../data-types/sbyte-data-type.md)  
  
- [<span data-ttu-id="5d5e2-109">UInteger – datový typ</span><span class="sxs-lookup"><span data-stu-id="5d5e2-109">UInteger Data Type</span></span>](../data-types/uinteger-data-type.md)  
  
- [<span data-ttu-id="5d5e2-110">ULong – datový typ</span><span class="sxs-lookup"><span data-stu-id="5d5e2-110">ULong Data Type</span></span>](../data-types/ulong-data-type.md)  
  
- [<span data-ttu-id="5d5e2-111">UShort – datový typ</span><span class="sxs-lookup"><span data-stu-id="5d5e2-111">UShort Data Type</span></span>](../data-types/ushort-data-type.md)  
  
 <span data-ttu-id="5d5e2-112">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="5d5e2-112">By default, this message is a warning.</span></span> <span data-ttu-id="5d5e2-113">Další informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="5d5e2-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="5d5e2-114">**ID chyby:** BC40032</span><span class="sxs-lookup"><span data-stu-id="5d5e2-114">**Error ID:** BC40032</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5d5e2-115">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="5d5e2-115">To correct this error</span></span>  
  
- <span data-ttu-id="5d5e2-116">Pokud vaše rozhraní komponenty pouze k jiným .NET Framework komponentám nebo není rozhraním žádné jiné součásti, nemusíte nic měnit.</span><span class="sxs-lookup"><span data-stu-id="5d5e2-116">If your component interfaces only with other .NET Framework components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
- <span data-ttu-id="5d5e2-117">Pokud procházíte s komponentou, která není zapsána pro .NET Framework, může být možné určit, buď pomocí reflexe, nebo z dokumentace, zda podporuje tento datový typ.</span><span class="sxs-lookup"><span data-stu-id="5d5e2-117">If you are interfacing with a component not written for the .NET Framework, you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="5d5e2-118">V takovém případě není nutné měnit žádné změny.</span><span class="sxs-lookup"><span data-stu-id="5d5e2-118">If it does, you do not need to change anything.</span></span>  
  
- <span data-ttu-id="5d5e2-119">Pokud procházejíte s komponentou, která nepodporuje tento datový typ, je nutné ji nahradit nejbližším typem odpovídajícím specifikaci CLS.</span><span class="sxs-lookup"><span data-stu-id="5d5e2-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="5d5e2-120">Například, `UInteger` `Integer` Pokud nepotřebujete rozsah hodnoty nad 2 147 483 647, můžete použít třeba místo.</span><span class="sxs-lookup"><span data-stu-id="5d5e2-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="5d5e2-121">Pokud budete potřebovat Rozšířený rozsah, můžete nahradit `UInteger` `Long` .</span><span class="sxs-lookup"><span data-stu-id="5d5e2-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
- <span data-ttu-id="5d5e2-122">Pokud procházíte s objekty automatizace nebo COM, pamatujte, že některé typy mají odlišnou šířku dat než v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5d5e2-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the .NET Framework.</span></span> <span data-ttu-id="5d5e2-123">Například `uint` obvykle je 16 bitů v jiných prostředích.</span><span class="sxs-lookup"><span data-stu-id="5d5e2-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="5d5e2-124">Pokud předáváte pro takovou součást 16bitový argument, deklarujte ji jako `UShort` místo `UInteger` ve spravovaném kódu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="5d5e2-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d5e2-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d5e2-125">See also</span></span>

- [<span data-ttu-id="5d5e2-126">Reflexe (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d5e2-126">Reflection (Visual Basic)</span></span>](../../programming-guide/concepts/reflection.md)
- [<span data-ttu-id="5d5e2-127">Reflexe</span><span class="sxs-lookup"><span data-stu-id="5d5e2-127">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)
