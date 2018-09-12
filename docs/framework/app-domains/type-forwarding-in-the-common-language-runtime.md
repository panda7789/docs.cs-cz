---
title: Předávání typů v modulu Common Language Runtime
ms.date: 03/30/2017
dev_langs:
- csharp
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], type forwarding
- type forwarding
ms.assetid: 51f8ffa3-c253-4201-a3d3-c4fad85ae097
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d25bac953ff68422a1dddc54bdb01b4b4f241cbb
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44509574"
---
# <a name="type-forwarding-in-the-common-language-runtime"></a><span data-ttu-id="2d4a3-102">Předávání typů v modulu Common Language Runtime</span><span class="sxs-lookup"><span data-stu-id="2d4a3-102">Type Forwarding in the Common Language Runtime</span></span>
<span data-ttu-id="2d4a3-103">Předávání typů vám umožní přesunout typu na jiné sestavení bez nutnosti znovu kompilovat aplikace, které používají původní sestavení.</span><span class="sxs-lookup"><span data-stu-id="2d4a3-103">Type forwarding allows you to move a type to another assembly without having to recompile applications that use the original assembly.</span></span>  
  
 <span data-ttu-id="2d4a3-104">Předpokládejme například, že aplikace používá `Example` třídy v sestavení s názvem `Utility.dll`.</span><span class="sxs-lookup"><span data-stu-id="2d4a3-104">For example, suppose an application uses the `Example` class in an assembly named `Utility.dll`.</span></span> <span data-ttu-id="2d4a3-105">Vývojáři `Utility.dll` rozhodnout Refaktorovat sestavení a v procesu může být přesunout `Example` třídy na jiné sestavení.</span><span class="sxs-lookup"><span data-stu-id="2d4a3-105">The developers of `Utility.dll` might decide to refactor the assembly, and in the process they might move the `Example` class to another assembly.</span></span> <span data-ttu-id="2d4a3-106">Pokud je starší verze této `Utility.dll` je nahrazena novou verzi `Utility.dll` a jeho sestavení doprovodné aplikace, která používá `Example` třídy se nezdaří, protože nelze nalézt `Example` třídy v nové verzi sady `Utility.dll`.</span><span class="sxs-lookup"><span data-stu-id="2d4a3-106">If the old version of `Utility.dll` is replaced by the new version of `Utility.dll` and its companion assembly, the application that uses the `Example` class fails because it cannot locate the `Example` class in the new version of `Utility.dll`.</span></span>  
  
 <span data-ttu-id="2d4a3-107">Vývojáři `Utility.dll` lze zabránit předá požadavky `Example` třídy pomocí <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="2d4a3-107">The developers of `Utility.dll` can avoid this by forwarding requests for the `Example` class, using the <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> attribute.</span></span> <span data-ttu-id="2d4a3-108">Pokud byl použit atribut na novou verzi `Utility.dll`, žádosti o `Example` třídy jsou předaný do sestavení, která nyní obsahuje třídu.</span><span class="sxs-lookup"><span data-stu-id="2d4a3-108">If the attribute has been applied to the new version of `Utility.dll`, requests for the `Example` class are forwarded to the assembly that now contains the class.</span></span> <span data-ttu-id="2d4a3-109">Existující aplikaci i nadále fungovat normálně, bez opětovnou kompilaci.</span><span class="sxs-lookup"><span data-stu-id="2d4a3-109">The existing application continues to function normally, without recompilation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d4a3-110">V rozhraní .NET Framework verze 2.0 nemohou předat dál typy ze sestavení, které jsou napsané v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="2d4a3-110">In the .NET Framework version 2.0, you cannot forward types from assemblies written in Visual Basic.</span></span> <span data-ttu-id="2d4a3-111">Aplikace napsané v jazyce Visual Basic však může spotřebovat předané typy.</span><span class="sxs-lookup"><span data-stu-id="2d4a3-111">However, an application written in Visual Basic can consume forwarded types.</span></span> <span data-ttu-id="2d4a3-112">To znamená pokud aplikace používá sestavení nakódovat v jazyce C# nebo C++ a typ v tomto sestavení je přemístěn na jiné sestavení, můžete použít aplikaci Visual Basic předaný typ.</span><span class="sxs-lookup"><span data-stu-id="2d4a3-112">That is, if the application uses an assembly coded in C# or C++, and a type from that assembly is forwarded to another assembly, the Visual Basic application can use the forwarded type.</span></span>  
  
## <a name="forwarding-types"></a><span data-ttu-id="2d4a3-113">Předávání typů</span><span class="sxs-lookup"><span data-stu-id="2d4a3-113">Forwarding Types</span></span>  
 <span data-ttu-id="2d4a3-114">Předávání typu čtyři kroky:</span><span class="sxs-lookup"><span data-stu-id="2d4a3-114">There are four steps to forwarding a type:</span></span>  
  
1.  <span data-ttu-id="2d4a3-115">Zdrojový kód pro typ přesuňte z původní sestavení do cílového sestavení.</span><span class="sxs-lookup"><span data-stu-id="2d4a3-115">Move the source code for the type from the original assembly to the destination assembly.</span></span>  
  
2.  <span data-ttu-id="2d4a3-116">V sestavení, kde lze najít typ, přidejte <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> pro typ, který byl přesunut.</span><span class="sxs-lookup"><span data-stu-id="2d4a3-116">In the assembly where the type used to be located, add a <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> for the type that was moved.</span></span> <span data-ttu-id="2d4a3-117">Následující kód ukazuje atributu pro typ s názvem `Example` , který byl přesunut.</span><span class="sxs-lookup"><span data-stu-id="2d4a3-117">The following code shows the attribute for a type named `Example` that was moved.</span></span>  
  
    ```csharp  
    [assembly:TypeForwardedToAttribute(typeof(Example))]  
    ```  
  
    ```cpp  
    [assembly:TypeForwardedToAttribute(Example::typeid)]  
    ```  
  
3.  <span data-ttu-id="2d4a3-118">Kompilace, která nyní obsahuje typ sestavení.</span><span class="sxs-lookup"><span data-stu-id="2d4a3-118">Compile the assembly that now contains the type.</span></span>  
  
4.  <span data-ttu-id="2d4a3-119">Znovu zkompilujte použití typu budou umístěné, s odkazem na sestavení, která nyní obsahuje typ sestavení.</span><span class="sxs-lookup"><span data-stu-id="2d4a3-119">Recompile the assembly where the type used to be located, with a reference to the assembly that now contains the type.</span></span> <span data-ttu-id="2d4a3-120">Například pokud kompilujete soubor jazyka C# z příkazového řádku, použijte [/Reference (možnosti kompilátoru C#)](~/docs/csharp/language-reference/compiler-options/reference-compiler-option.md) možnost určit, který obsahuje typ sestavení.</span><span class="sxs-lookup"><span data-stu-id="2d4a3-120">For example, if you are compiling a C# file from the command line, use the [/reference (C# Compiler Options)](~/docs/csharp/language-reference/compiler-options/reference-compiler-option.md) option to specify the assembly that contains the type.</span></span> <span data-ttu-id="2d4a3-121">V jazyce C++, použijte [#using](https://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a) směrnice ve zdrojovém souboru k určení, která obsahuje typ sestavení.</span><span class="sxs-lookup"><span data-stu-id="2d4a3-121">In C++, use the [#using](https://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a) directive in the source file to specify the assembly that contains the type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d4a3-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="2d4a3-122">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>  
 [<span data-ttu-id="2d4a3-123">Předávání typů (C++/CLI)</span><span class="sxs-lookup"><span data-stu-id="2d4a3-123">Type Forwarding (C++/CLI)</span></span>](/cpp/windows/type-forwarding-cpp-cli)  
 [<span data-ttu-id="2d4a3-124">#using – direktiva</span><span class="sxs-lookup"><span data-stu-id="2d4a3-124">#using Directive</span></span>](https://msdn.microsoft.com/library/870b15e5-f361-40a8-ba1c-c57d75c8809a)
