---
title: "Typ člena & č. 39; &lt;membername&gt;& č. 39; není kompatibilní se specifikací CLS"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc40025
- vbc40025
helpviewer_keywords: BC40025
ms.assetid: adbd34bb-43d2-4266-90e7-cd1afaf49b4e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9f7121d4787ce36feb6de5f08ca60a4419877f98
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="type-of-member-39ltmembernamegt39-is-not-cls-compliant"></a><span data-ttu-id="ad877-102">Typ člena & č. 39; &lt;membername&gt;& č. 39; není kompatibilní se specifikací CLS</span><span class="sxs-lookup"><span data-stu-id="ad877-102">Type of member &#39;&lt;membername&gt;&#39; is not CLS-compliant</span></span>
<span data-ttu-id="ad877-103">Datový typ zadaný pro tento člen není součástí [jazyková nezávislost a jazykově nezávislé komponenty](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="ad877-103">The data type specified for this member is not part of the [Language Independence and Language-Independent Components](../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS).</span></span> <span data-ttu-id="ad877-104">Toto není chybu v rámci komponenty, protože [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] podporují tento datový typ.</span><span class="sxs-lookup"><span data-stu-id="ad877-104">This is not an error within your component, because the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] and [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] support this data type.</span></span> <span data-ttu-id="ad877-105">Jiné komponenty, které jsou zapsané ve výhradně kompatibilní se specifikací CLS kódu však nemusí podporovat tento datový typ.</span><span class="sxs-lookup"><span data-stu-id="ad877-105">However, another component written in strictly CLS-compliant code might not support this data type.</span></span> <span data-ttu-id="ad877-106">Tyto součásti nemusí být možné úspěšně komunikovat s příslušné součásti.</span><span class="sxs-lookup"><span data-stu-id="ad877-106">Such a component might not be able to interact successfully with your component.</span></span>  
  
 <span data-ttu-id="ad877-107">Následující [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] datové typy nejsou kompatibilní se specifikací CLS:</span><span class="sxs-lookup"><span data-stu-id="ad877-107">The following [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] data types are not CLS-compliant:</span></span>  
  
-   [<span data-ttu-id="ad877-108">SByte – datový typ</span><span class="sxs-lookup"><span data-stu-id="ad877-108">SByte Data Type</span></span>](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)  
  
-   [<span data-ttu-id="ad877-109">Uinteger – datový typ</span><span class="sxs-lookup"><span data-stu-id="ad877-109">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
  
-   [<span data-ttu-id="ad877-110">Ulong – datový typ</span><span class="sxs-lookup"><span data-stu-id="ad877-110">ULong Data Type</span></span>](../../../visual-basic/language-reference/data-types/ulong-data-type.md)  
  
-   [<span data-ttu-id="ad877-111">Ushort – datový typ</span><span class="sxs-lookup"><span data-stu-id="ad877-111">UShort Data Type</span></span>](../../../visual-basic/language-reference/data-types/ushort-data-type.md)  
  
 <span data-ttu-id="ad877-112">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="ad877-112">By default, this message is a warning.</span></span> <span data-ttu-id="ad877-113">Další informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="ad877-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="ad877-114">**ID chyby:** BC40025</span><span class="sxs-lookup"><span data-stu-id="ad877-114">**Error ID:** BC40025</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ad877-115">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ad877-115">To correct this error</span></span>  
  
-   <span data-ttu-id="ad877-116">Pokud příslušné součásti rozhraní pouze s jinými [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] součástí, nebo nemá není rozhraní s ostatními součástmi, není potřeba nic nezmění.</span><span class="sxs-lookup"><span data-stu-id="ad877-116">If your component interfaces only with other [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] components, or does not interface with any other components, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="ad877-117">Pokud se propojení s nejsou určeny pro součásti [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], je možné určit, buď pomocí reflexe nebo z dokumentace, jestli podporuje tento datový typ.</span><span class="sxs-lookup"><span data-stu-id="ad877-117">If you are interfacing with a component not written for the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], you might be able to determine, either through reflection or from documentation, whether it supports this data type.</span></span> <span data-ttu-id="ad877-118">Pokud ano, není potřeba nic nezmění.</span><span class="sxs-lookup"><span data-stu-id="ad877-118">If it does, you do not need to change anything.</span></span>  
  
-   <span data-ttu-id="ad877-119">Pokud se propojení s komponenty, která nepodporuje tento typ dat, musíte jej nahradit s typem nejbližší kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="ad877-119">If you are interfacing with a component that does not support this data type, you must replace it with the closest CLS-compliant type.</span></span> <span data-ttu-id="ad877-120">Například v místě z `UInteger` je možné použít `Integer` Pokud nepotřebujete rozsah hodnot výše 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="ad877-120">For example, in place of `UInteger` you might be able to use `Integer` if you do not need the value range above 2,147,483,647.</span></span> <span data-ttu-id="ad877-121">Pokud potřebujete rozšířené rozsahu, můžete nahradit `UInteger` s `Long`.</span><span class="sxs-lookup"><span data-stu-id="ad877-121">If you do need the extended range, you can replace `UInteger` with `Long`.</span></span>  
  
-   <span data-ttu-id="ad877-122">Pokud se propojení s objekty automatizace nebo COM, mějte na paměti, že některé typy mají různé datové šířek než [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ad877-122">If you are interfacing with Automation or COM objects, keep in mind that some types have different data widths than in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="ad877-123">Například `uint` je často 16 bitů v jiných prostředích.</span><span class="sxs-lookup"><span data-stu-id="ad877-123">For example, `uint` is often 16 bits in other environments.</span></span> <span data-ttu-id="ad877-124">Argument 16bitové předáte pro tyto součásti, deklarujte ji jako `UShort` místo `UInteger` ve vaší spravované [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kódu.</span><span class="sxs-lookup"><span data-stu-id="ad877-124">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad877-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad877-125">See Also</span></span>  
 [<span data-ttu-id="ad877-126">Reflexe</span><span class="sxs-lookup"><span data-stu-id="ad877-126">Reflection</span></span>](../../../framework/reflection-and-codedom/reflection.md)  
 [<span data-ttu-id="ad877-127">\<PAVE přes > zápis kompatibilní se specifikací CLS kódu</span><span class="sxs-lookup"><span data-stu-id="ad877-127">\<PAVE OVER> Writing CLS-Compliant Code</span></span>](http://msdn.microsoft.com/en-us/4c705105-69a2-4e5e-b24e-0633bc32c7f3)
