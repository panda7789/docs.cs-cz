---
title: Předávání typů v modulu CLR (Common Language Runtime)
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
dev_langs:
- csharp
- cpp
ms.openlocfilehash: 215636a9617a2723d8ab69640c1d3e69491a7d87
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160362"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a><span data-ttu-id="3e8ae-102">Předávání typů v modulu CLR (Common Language Runtime)</span><span class="sxs-lookup"><span data-stu-id="3e8ae-102">Type forwarding in the common language runtime</span></span>
<span data-ttu-id="3e8ae-103">Předávání typů umožňuje přesunout typ do jiného sestavení bez nutnosti překompilovat aplikace, které používají původní sestavení.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-103">Type forwarding allows you to move a type to another assembly without having to recompile applications that use the original assembly.</span></span>  
  
 <span data-ttu-id="3e8ae-104">Předpokládejme například, že `Example` aplikace používá třídu v sestavení s názvem *Utility.dll*.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-104">For example, suppose an application uses the `Example` class in an assembly named *Utility.dll*.</span></span> <span data-ttu-id="3e8ae-105">Vývojáři *utility.dll* může rozhodnout o refaktorování sestavení a `Example` v procesu mohou přesunout třídu do jiného sestavení.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-105">The developers of *Utility.dll* might decide to refactor the assembly, and in the process they might move the `Example` class to another assembly.</span></span> <span data-ttu-id="3e8ae-106">Pokud je stará verze služby *Utility.dll* nahrazena novou verzí souboru *Utility.dll* `Example` a jejím doprovodným `Example` sestavením, aplikace, která používá třídu, se nezdaří, protože nemůže najít třídu v nové verzi *souboru Utility.dll*.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-106">If the old version of *Utility.dll* is replaced by the new version of *Utility.dll* and its companion assembly, the application that uses the `Example` class fails because it cannot locate the `Example` class in the new version of *Utility.dll*.</span></span>  
  
 <span data-ttu-id="3e8ae-107">Vývojáři *Utility.dll* můžete vyhnout tím, že `Example` předávání požadavků <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> pro třídu pomocí atributu.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-107">The developers of *Utility.dll* can avoid this by forwarding requests for the `Example` class, using the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribute.</span></span> <span data-ttu-id="3e8ae-108">Pokud byl atribut použit pro novou verzi *služby Utility.dll*, požadavky na třídu `Example` jsou předány sestavení, které nyní obsahuje třídu.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-108">If the attribute has been applied to the new version of *Utility.dll*, requests for the `Example` class are forwarded to the assembly that now contains the class.</span></span> <span data-ttu-id="3e8ae-109">Existující aplikace nadále fungovat normálně, bez rekompilace.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-109">The existing application continues to function normally, without recompilation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3e8ae-110">V rozhraní .NET Framework verze 2.0 nelze předávat typy ze sestavení napsaných v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-110">In the .NET Framework version 2.0, you cannot forward types from assemblies written in Visual Basic.</span></span> <span data-ttu-id="3e8ae-111">Aplikace napsaná v jazyce Visual Basic však může využívat předané typy.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-111">However, an application written in Visual Basic can consume forwarded types.</span></span> <span data-ttu-id="3e8ae-112">To znamená, že pokud aplikace používá sestavení kódované v jazyce C# nebo C++ a typ z tohoto sestavení je předán do jiného sestavení, aplikace jazyka visual basic můžete použít předaný typ.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-112">That is, if the application uses an assembly coded in C# or C++, and a type from that assembly is forwarded to another assembly, the Visual Basic application can use the forwarded type.</span></span>  
  
## <a name="forward-types"></a><span data-ttu-id="3e8ae-113">Dopředné typy</span><span class="sxs-lookup"><span data-stu-id="3e8ae-113">Forward types</span></span>  
 <span data-ttu-id="3e8ae-114">Existují čtyři kroky k předávání typu:</span><span class="sxs-lookup"><span data-stu-id="3e8ae-114">There are four steps to forwarding a type:</span></span>  
  
1. <span data-ttu-id="3e8ae-115">Přesuňte zdrojový kód pro typ z původního sestavení do cílového sestavení.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-115">Move the source code for the type from the original assembly to the destination assembly.</span></span>  

2. <span data-ttu-id="3e8ae-116">V sestavě, kde byl typ umístěn, přidejte a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> pro typ, který byl přesunut.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-116">In the assembly where the type used to be located, add a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> for the type that was moved.</span></span> <span data-ttu-id="3e8ae-117">Následující kód zobrazuje atribut pro `Example` typ s názvem, který byl přesunut.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-117">The following code shows the attribute for a type named `Example` that was moved.</span></span>  

   ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
   ```

   ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
   ```  

3. <span data-ttu-id="3e8ae-118">Zkompilujte sestavení, které nyní obsahuje typ.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-118">Compile the assembly that now contains the type.</span></span>  

4. <span data-ttu-id="3e8ae-119">Překompilujte sestavení, kde typ slouží k umístění, s odkazem na sestavení, které nyní obsahuje typ.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-119">Recompile the assembly where the type used to be located, with a reference to the assembly that now contains the type.</span></span> <span data-ttu-id="3e8ae-120">Například pokud sestavujete soubor Jazyka C# z příkazového řádku, použijte možnost [-reference (C# kompilátor)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) k určení sestavení, které obsahuje typ.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-120">For example, if you are compiling a C# file from the command line, use the [-reference (C# compiler options)](../../csharp/language-reference/compiler-options/reference-compiler-option.md) option to specify the assembly that contains the type.</span></span> <span data-ttu-id="3e8ae-121">V jazyce C++ použijte direktivu [#using](/cpp/preprocessor/hash-using-directive-cpp) ve zdrojovém souboru k určení sestavení, které obsahuje typ.</span><span class="sxs-lookup"><span data-stu-id="3e8ae-121">In C++, use the [#using](/cpp/preprocessor/hash-using-directive-cpp) directive in the source file to specify the assembly that contains the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e8ae-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e8ae-122">See also</span></span>

- <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>
- [<span data-ttu-id="3e8ae-123">Předávání typů (C++/CLI)</span><span class="sxs-lookup"><span data-stu-id="3e8ae-123">Type forwarding (C++/CLI)</span></span>](/cpp/windows/type-forwarding-cpp-cli)
- [<span data-ttu-id="3e8ae-124">směrnice o #using</span><span class="sxs-lookup"><span data-stu-id="3e8ae-124">#using directive</span></span>](/cpp/preprocessor/hash-using-directive-cpp)
