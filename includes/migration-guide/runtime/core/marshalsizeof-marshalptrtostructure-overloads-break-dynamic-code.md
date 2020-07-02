---
ms.openlocfilehash: c462c7b4ec8423ce8fd331d3cd31154283cf1f1d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619987"
---
### <a name="marshalsizeof-and-marshalptrtostructure-overloads-break-dynamic-code"></a><span data-ttu-id="a125c-101">Marshaling. SizeOf a Marshal. PtrToStructure přetížení dynamického kódu</span><span class="sxs-lookup"><span data-stu-id="a125c-101">Marshal.SizeOf and Marshal.PtrToStructure overloads break dynamic code</span></span>

#### <a name="details"></a><span data-ttu-id="a125c-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a125c-102">Details</span></span>

<span data-ttu-id="a125c-103">Počínaje .NET Framework 4.5.1, dynamicky navázání na metody,,,, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601> <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)> <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)> <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)> <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)> , nebo <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)> (například prostřednictvím prostředí Windows PowerShell, ironpythonu nebo dynamické klíčové slovo C#) může mít za následek <code>MethodInvocationExceptions</code> to, že se přidala nová přetížení těchto metod, která můžou být nejednoznačná pro skriptovací stroje.</span><span class="sxs-lookup"><span data-stu-id="a125c-103">Beginning in the .NET Framework 4.5.1, dynamically binding to the methods <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601>, <xref:System.Runtime.InteropServices.Marshal.SizeOf%60%601(%60%600)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Object)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure(System.IntPtr,System.Type)>, <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr)>, or <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%60%601(System.IntPtr,%60%600)>, (via Windows PowerShell, IronPython, or the C# dynamic keyword, for example) can result in <code>MethodInvocationExceptions</code> because new overloads of these methods have been added that may be ambiguous to the scripting engines.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a125c-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="a125c-104">Suggestion</span></span>

<span data-ttu-id="a125c-105">Aktualizujte skripty, aby jasně označovaly, které přetížení by mělo být použito.</span><span class="sxs-lookup"><span data-stu-id="a125c-105">Update scripts to clearly indicate which overload should be used.</span></span> <span data-ttu-id="a125c-106">To se obvykle může provést explicitním přetypováním parametrů typu metody jako <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="a125c-106">This can typically done by explicitly casting the methods' type parameters as <xref:System.Type>.</span></span> <span data-ttu-id="a125c-107">Další podrobnosti a příklady, jak tento problém vyřešit, najdete v [tomto odkazu](https://support.microsoft.com/kb/2909958/) .</span><span class="sxs-lookup"><span data-stu-id="a125c-107">See [this link](https://support.microsoft.com/kb/2909958/) for more detail and examples of how to workaround the issue.</span></span>

| <span data-ttu-id="a125c-108">Name</span><span class="sxs-lookup"><span data-stu-id="a125c-108">Name</span></span>    | <span data-ttu-id="a125c-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="a125c-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a125c-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="a125c-110">Scope</span></span>   |<span data-ttu-id="a125c-111">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="a125c-111">Minor</span></span>|
|<span data-ttu-id="a125c-112">Verze</span><span class="sxs-lookup"><span data-stu-id="a125c-112">Version</span></span>|<span data-ttu-id="a125c-113">4.5.1</span><span class="sxs-lookup"><span data-stu-id="a125c-113">4.5.1</span></span>|
|<span data-ttu-id="a125c-114">Typ</span><span class="sxs-lookup"><span data-stu-id="a125c-114">Type</span></span>|<span data-ttu-id="a125c-115">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="a125c-115">Runtime</span></span>|
