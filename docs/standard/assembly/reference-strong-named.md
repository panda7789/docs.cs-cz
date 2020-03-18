---
title: 'Postup: Odkaz na sestavení se silným názvem'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: adda4ed2ab5c59e3518b8e724044529a79840ad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78156475"
---
# <a name="how-to-reference-a-strong-named-assembly"></a><span data-ttu-id="9a013-102">Postup: Odkaz na sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="9a013-102">How to: Reference a strong-named assembly</span></span>
<span data-ttu-id="9a013-103">Proces odkazování na typy nebo prostředky v sestavení se silným názvem je obvykle transparentní.</span><span class="sxs-lookup"><span data-stu-id="9a013-103">The process for referencing types or resources in a strong-named assembly is usually transparent.</span></span> <span data-ttu-id="9a013-104">Můžete provést odkaz buď v době kompilace (brzy vazby) nebo v době běhu.</span><span class="sxs-lookup"><span data-stu-id="9a013-104">You can make the reference either at compile time (early binding) or at run time.</span></span>  
  
<span data-ttu-id="9a013-105">Odkaz na dobu kompilace dojde, když označíte kompilátoru, že sestavení, které má být kompilován explicitně odkazuje na jiné sestavení.</span><span class="sxs-lookup"><span data-stu-id="9a013-105">A compile-time reference occurs when you indicate to the compiler that the assembly to be compiled explicitly references another assembly.</span></span> <span data-ttu-id="9a013-106">Při použití odkazování v době kompilace kompilátor automaticky získá veřejný klíč cílové sestavení se silným názvem a umístí jej do odkazu sestavení sestavení, které je kompilován.</span><span class="sxs-lookup"><span data-stu-id="9a013-106">When you use compile-time referencing, the compiler automatically gets the public key of the targeted strong-named assembly and places it in the assembly reference of the assembly being compiled.</span></span>
  
> [!NOTE]
> <span data-ttu-id="9a013-107">Sestavení se silným názvem může používat pouze typy z jiných sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="9a013-107">A strong-named assembly can only use types from other strong-named assemblies.</span></span> <span data-ttu-id="9a013-108">V opačném případě by byla ohrožena bezpečnost sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="9a013-108">Otherwise, the security of the strong-named assembly would be compromised.</span></span>  
  
## <a name="make-a-compile-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="9a013-109">Vytvořte odkaz na sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="9a013-109">Make a compile-time reference to a strong-named assembly</span></span>  

<span data-ttu-id="9a013-110">Do příkazového řádku zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="9a013-110">At a command prompt, type the following command:</span></span>  

<span data-ttu-id="9a013-111">\<*příkaz*> kompilátoru **/reference:**\<*název sestavení*></span><span class="sxs-lookup"><span data-stu-id="9a013-111">\<*compiler command*> **/reference:**\<*assembly name*></span></span>  

<span data-ttu-id="9a013-112">V tomto příkazu je *příkaz kompilátoru* příkaz kompilátoru pro jazyk, který používáte, a *název sestavení* je název sestavení se silným názvem, na které se odkazuje.</span><span class="sxs-lookup"><span data-stu-id="9a013-112">In this command, *compiler command* is the compiler command for the language you are using, and *assembly name* is the name of the strong-named assembly being referenced.</span></span> <span data-ttu-id="9a013-113">Můžete také použít jiné možnosti kompilátoru, jako je například možnost **/t:library** pro vytvoření sestavení knihovny.</span><span class="sxs-lookup"><span data-stu-id="9a013-113">You can also use other compiler options, such as the **/t:library** option for creating a library assembly.</span></span>  

<span data-ttu-id="9a013-114">Následující příklad vytvoří sestavení s názvem *myAssembly.dll,* které odkazuje na sestavení se silným názvem s názvem *myLibAssembly.dll* z modulu kódu s názvem *myAssembly.cs*.</span><span class="sxs-lookup"><span data-stu-id="9a013-114">The following example creates an assembly called *myAssembly.dll* that references a strong-named assembly called *myLibAssembly.dll* from a code module called *myAssembly.cs*.</span></span>  

```cmd
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  

## <a name="make-a-run-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="9a013-115">Vytvoření odkazu za běhu na sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="9a013-115">Make a run-time reference to a strong-named assembly</span></span>  
  
<span data-ttu-id="9a013-116">Při vytvoření odkazu za běhu na sestavení se silným názvem, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> například pomocí metody nebo, musíte použít zobrazovaný název odkazovaného sestavení se silným názvem.</span><span class="sxs-lookup"><span data-stu-id="9a013-116">When you make a run-time reference to a strong-named assembly, for example by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> method, you must use the display name of the referenced strong-named assembly.</span></span> <span data-ttu-id="9a013-117">Syntaxe zobrazovaného názvu je následující:</span><span class="sxs-lookup"><span data-stu-id="9a013-117">The syntax of a display name is as follows:</span></span>  

<span data-ttu-id="9a013-118">\<*název*>sestavení **,** \< *číslo*>verze **,** \< *jazyková verze*>**,** \<token *veřejného klíče*></span><span class="sxs-lookup"><span data-stu-id="9a013-118">\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*></span></span>  

<span data-ttu-id="9a013-119">Například:</span><span class="sxs-lookup"><span data-stu-id="9a013-119">For example:</span></span>  

```console
myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33
```  

<span data-ttu-id="9a013-120">V tomto `PublicKeyToken` příkladu je šestnáctková forma tokenu veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="9a013-120">In this example, `PublicKeyToken` is the hexadecimal form of the public key token.</span></span> <span data-ttu-id="9a013-121">Pokud neexistuje žádná hodnota `Culture=neutral`jazykové verze, použijte .</span><span class="sxs-lookup"><span data-stu-id="9a013-121">If there is no culture value, use `Culture=neutral`.</span></span>  

<span data-ttu-id="9a013-122">Následující příklad kódu ukazuje, jak používat <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> tyto informace s metodou.</span><span class="sxs-lookup"><span data-stu-id="9a013-122">The following code example shows how to use this information with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  

```cpp
Assembly^ myDll =
    Assembly::Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1");
```

```csharp
Assembly myDll =
    Assembly.Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1");
```

```vb
Dim myDll As Assembly = _
    Assembly.Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1")
```

<span data-ttu-id="9a013-123">Šestnáctkový formát veřejného klíče a tokenveřejného klíče pro konkrétní sestavení můžete vytisknout pomocí následujícího příkazu [Silný název (Sn.exe):](../../framework/tools/sn-exe-strong-name-tool.md)</span><span class="sxs-lookup"><span data-stu-id="9a013-123">You can print the hexadecimal format of the public key and public key token for a specific assembly by using the following [Strong Name (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) command:</span></span>  

<span data-ttu-id="9a013-124">**sn \< -Tp** *sestava\*\*\*>*\*</span><span class="sxs-lookup"><span data-stu-id="9a013-124">**sn -Tp \<** *assembly* **>**</span></span>  

<span data-ttu-id="9a013-125">Pokud máte soubor veřejného klíče, můžete místo toho použít následující příkaz (všimněte si rozdílu v případě volby příkazového řádku):</span><span class="sxs-lookup"><span data-stu-id="9a013-125">If you have a public key file, you can use the following command instead (note the difference in case on the command-line option):</span></span>  

<span data-ttu-id="9a013-126">\**sn -tp \< \*\* *soubor veřejného klíče\*\*\*>**</span><span class="sxs-lookup"><span data-stu-id="9a013-126">**sn -tp \<** *public key file* **>**</span></span>  

## <a name="see-also"></a><span data-ttu-id="9a013-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="9a013-127">See also</span></span>

- [<span data-ttu-id="9a013-128">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="9a013-128">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
