---
title: -publicsign (možnosti kompilátoru C#)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: ec25f9c1f2ef943db41bcfa20c8efd1d05866acd
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/24/2018
---
# <a name="-publicsign-c-compiler-options"></a><span data-ttu-id="1908d-102">-publicsign (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="1908d-102">-publicsign (C# Compiler Options)</span></span>

<span data-ttu-id="1908d-103">Tato možnost způsobí, že kompilátor veřejný klíč použít, ale není ve skutečnosti podepsání sestavení.</span><span class="sxs-lookup"><span data-stu-id="1908d-103">This option causes the compiler to apply a public key but does not actually sign the assembly.</span></span> <span data-ttu-id="1908d-104">**- Publicsign** možnost nastaví trochu v sestavení, které modul runtime informuje, že soubor je ve skutečnosti podepsaná.</span><span class="sxs-lookup"><span data-stu-id="1908d-104">The **-publicsign** option also sets a bit in the assembly that tells the runtime that the file is actually signed.</span></span>

## <a name="syntax"></a><span data-ttu-id="1908d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1908d-105">Syntax</span></span>

```console
-publicsign
```

## <a name="arguments"></a><span data-ttu-id="1908d-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="1908d-106">Arguments</span></span>

<span data-ttu-id="1908d-107">Žádné</span><span class="sxs-lookup"><span data-stu-id="1908d-107">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="1908d-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1908d-108">Remarks</span></span>

<span data-ttu-id="1908d-109">**- Publicsign** možnost vyžaduje použití [- keyfile](keyfile-compiler-option.md) nebo [- keycontainer](keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="1908d-109">The **-publicsign** option requires the use of the [-keyfile](keyfile-compiler-option.md) or [-keycontainer](keycontainer-compiler-option.md).</span></span> <span data-ttu-id="1908d-110">**Keyfile** nebo **keycontainer** možnosti zadejte veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="1908d-110">The **keyfile** or **keycontainer** options specify the public key.</span></span>

<span data-ttu-id="1908d-111">**- Publicsign** a **- delaysign** možnosti se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="1908d-111">The **-publicsign** and **-delaysign** options are mutually exclusive.</span></span>

<span data-ttu-id="1908d-112">Někdy označuje jako "falešných přihlášení" nebo "Přihlášení OSS", veřejné podepisování obsahuje veřejný klíč ve výstupu sestavení a nastavuje příznak "podepsaný", ale není ve skutečnosti podepsání sestavení s privátním klíčem.</span><span class="sxs-lookup"><span data-stu-id="1908d-112">Sometimes called "fake sign" or "OSS sign", public signing includes the public key in an output assembly and sets the "signed" flag, but doesn't actually sign the assembly with a private key.</span></span> <span data-ttu-id="1908d-113">To je užitečné pro projekty s otevřeným zdrojem, kde chcete vytvořit sestavení, které jsou kompatibilní s vydaná "plně podepsaný, sestavení, ale nemáte přístup k privátnímu klíči použité k podepsání sestavení osoby.</span><span class="sxs-lookup"><span data-stu-id="1908d-113">This is useful for open source projects where people want to build assemblies which are compatible with the released "fully signed" assemblies, but don't have access to the private key used to sign the assemblies.</span></span> <span data-ttu-id="1908d-114">Vzhledem k tomu, že téměř žádné příjemce skutečně potřeba zkontrolovat, pokud je plně podepsáno sestavení, jsou veřejně předdefinované sestavení funkční v téměř každý scénář, kde se použije plně podepsané jeden.</span><span class="sxs-lookup"><span data-stu-id="1908d-114">Since almost no consumers actually need to check if the assembly is fully signed, these publicly built assemblies are useable in almost every scenario where the fully signed one would be used.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="1908d-115">Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1908d-115">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="1908d-116">Otevřete **vlastnosti** stránky pro projekt.</span><span class="sxs-lookup"><span data-stu-id="1908d-116">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="1908d-117">Změnit **zpoždění podepsání** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1908d-117">Modify the **Delay sign only** property.</span></span>

## <a name="see-also"></a><span data-ttu-id="1908d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="1908d-118">See Also</span></span>
 [<span data-ttu-id="1908d-119">-Delaysign – možnost kompilátor jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1908d-119">C# Compiler -delaysign option</span></span>](delaysign-compiler-option.md)  
 [<span data-ttu-id="1908d-120">-Keyfile – možnost kompilátor jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1908d-120">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)  
 [<span data-ttu-id="1908d-121">-Keycontainer – možnost kompilátor jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1908d-121">C# Compiler -keycontainer option</span></span>](keycontainer-compiler-option.md)  
 [<span data-ttu-id="1908d-122">Možnosti kompilátoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1908d-122">C# Compiler Options</span></span>](index.md)  
 [<span data-ttu-id="1908d-123">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="1908d-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
