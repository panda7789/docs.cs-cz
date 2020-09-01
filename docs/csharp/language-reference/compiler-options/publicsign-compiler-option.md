---
description: -publicsign (možnosti kompilátoru C#)
title: -publicsign (možnosti kompilátoru C#)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: 525912c7f50aa6b51e602be7b9258f1f5907daac
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89124809"
---
# <a name="-publicsign-c-compiler-options"></a><span data-ttu-id="b1bec-103">-publicsign (možnosti kompilátoru C#)</span><span class="sxs-lookup"><span data-stu-id="b1bec-103">-publicsign (C# Compiler Options)</span></span>

<span data-ttu-id="b1bec-104">Tato možnost způsobí, že kompilátor použije veřejný klíč, ale ve skutečnosti nepodepíše sestavení.</span><span class="sxs-lookup"><span data-stu-id="b1bec-104">This option causes the compiler to apply a public key but does not actually sign the assembly.</span></span> <span data-ttu-id="b1bec-105">Možnost **-publicsign** také nastavuje bitovou kopii v sestavení, která oznamuje modulu runtime, že soubor je skutečně podepsán.</span><span class="sxs-lookup"><span data-stu-id="b1bec-105">The **-publicsign** option also sets a bit in the assembly that tells the runtime that the file is actually signed.</span></span>

## <a name="syntax"></a><span data-ttu-id="b1bec-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1bec-106">Syntax</span></span>

```console
-publicsign
```

## <a name="arguments"></a><span data-ttu-id="b1bec-107">Argumenty</span><span class="sxs-lookup"><span data-stu-id="b1bec-107">Arguments</span></span>

<span data-ttu-id="b1bec-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="b1bec-108">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="b1bec-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1bec-109">Remarks</span></span>

<span data-ttu-id="b1bec-110">Možnost **-publicsign** vyžaduje použití souboru [-keyfile](keyfile-compiler-option.md) nebo [-klíče obsahujícího](keycontainer-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="b1bec-110">The **-publicsign** option requires the use of the [-keyfile](keyfile-compiler-option.md) or [-keycontainer](keycontainer-compiler-option.md).</span></span> <span data-ttu-id="b1bec-111">**Možnosti souboru** **keyfile nebo klíče** určují veřejný klíč.</span><span class="sxs-lookup"><span data-stu-id="b1bec-111">The **keyfile** or **keycontainer** options specify the public key.</span></span>

<span data-ttu-id="b1bec-112">Možnosti **-publicsign** a **-delaysign** se vzájemně vylučují.</span><span class="sxs-lookup"><span data-stu-id="b1bec-112">The **-publicsign** and **-delaysign** options are mutually exclusive.</span></span>

<span data-ttu-id="b1bec-113">Při veřejném zápisu se někdy označuje jako "falešné znaménko" nebo "znak OSS", ale veřejný podpis zahrnuje veřejný klíč ve výstupním sestavení a nastavuje příznak "signed", ale ve skutečnosti nepodepisuje sestavení pomocí privátního klíče.</span><span class="sxs-lookup"><span data-stu-id="b1bec-113">Sometimes called "fake sign" or "OSS sign", public signing includes the public key in an output assembly and sets the "signed" flag, but doesn't actually sign the assembly with a private key.</span></span> <span data-ttu-id="b1bec-114">To je užitečné pro open source projekty, kde lidé chtějí sestavovat sestavení, která jsou kompatibilní s vydanými sestaveními "plně podepsaný", ale nemají přístup k privátnímu klíči, který se používá k podepsání sestavení.</span><span class="sxs-lookup"><span data-stu-id="b1bec-114">This is useful for open source projects where people want to build assemblies which are compatible with the released "fully signed" assemblies, but don't have access to the private key used to sign the assemblies.</span></span> <span data-ttu-id="b1bec-115">Vzhledem k tomu, že téměř žádní spotřebitelé nepotřebují ověřit, jestli je sestavení plně podepsané, tato veřejně vytvořená sestavení jsou použitelná v téměř každém scénáři, kde se používá plně podepsaný certifikát.</span><span class="sxs-lookup"><span data-stu-id="b1bec-115">Since almost no consumers actually need to check if the assembly is fully signed, these publicly built assemblies are useable in almost every scenario where the fully signed one would be used.</span></span>

### <a name="to-set-this-compiler-option-in-a-csproj-file"></a><span data-ttu-id="b1bec-116">Nastavení této možnosti kompilátoru v souboru csproj</span><span class="sxs-lookup"><span data-stu-id="b1bec-116">To set this compiler option in a csproj file</span></span>

<span data-ttu-id="b1bec-117">Otevřete soubor. csproj pro projekt a přidejte následující element:</span><span class="sxs-lookup"><span data-stu-id="b1bec-117">Open the .csproj file for a project, and add the following element:</span></span>

```xml
<PublicSign>true</PublicSign>
```

## <a name="see-also"></a><span data-ttu-id="b1bec-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1bec-118">See also</span></span>

- [<span data-ttu-id="b1bec-119">Kompilátor C# – možnost delaysign</span><span class="sxs-lookup"><span data-stu-id="b1bec-119">C# Compiler -delaysign option</span></span>](delaysign-compiler-option.md)
- [<span data-ttu-id="b1bec-120">C# – možnost kompilátoru – parametr keyfile</span><span class="sxs-lookup"><span data-stu-id="b1bec-120">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)
- [<span data-ttu-id="b1bec-121">Kompilátor C# – možnost obsahuje</span><span class="sxs-lookup"><span data-stu-id="b1bec-121">C# Compiler -keycontainer option</span></span>](keycontainer-compiler-option.md)
- [<span data-ttu-id="b1bec-122">Možnosti kompilátoru C#</span><span class="sxs-lookup"><span data-stu-id="b1bec-122">C# Compiler Options</span></span>](index.md)
- [<span data-ttu-id="b1bec-123">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="b1bec-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
