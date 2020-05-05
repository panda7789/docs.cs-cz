---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74644045"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a><span data-ttu-id="5b3d6-101">Změna přístupu pro třída AccessibleObject. RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="5b3d6-101">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>

<span data-ttu-id="5b3d6-102">Od verze .NET Core 3,0 RC1 se přístupnost `AccessibleObject.RuntimeIDFirstItem` pro změnila z `protected` na. `internal`</span><span class="sxs-lookup"><span data-stu-id="5b3d6-102">Starting in .NET Core 3.0 RC1, the accessibility of `AccessibleObject.RuntimeIDFirstItem` has changed from `protected` to `internal`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5b3d6-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="5b3d6-103">Change description</span></span>

<span data-ttu-id="5b3d6-104">Od verze .NET Core 3,0 Preview 4 bylo `AccessibleObject.RuntimeIDFirstItem` `protected`pole.</span><span class="sxs-lookup"><span data-stu-id="5b3d6-104">Starting with .NET Core 3.0 Preview 4, the `AccessibleObject.RuntimeIDFirstItem` field was `protected`.</span></span> <span data-ttu-id="5b3d6-105">Od verze .NET Core 3,0 RC1 se změnila z `protected` verze na `internal` , aby byla zarovnaná s přístupností pole v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5b3d6-105">Starting with .NET Core 3.0 RC1, it has changed from `protected` to `internal` to align with the accessibility of the field in the .NET Framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5b3d6-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="5b3d6-106">Version introduced</span></span>

<span data-ttu-id="5b3d6-107">3,0 RC1</span><span class="sxs-lookup"><span data-stu-id="5b3d6-107">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5b3d6-108">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="5b3d6-108">Recommended action</span></span>

<span data-ttu-id="5b3d6-109">Tato změna může mít vliv na to, zda jste vytvořili aplikaci .NET Core s typem, který je odvozen <xref:System.Windows.Forms.AccessibleObject> z a přistupuje k `RuntimeIDFirstItem` poli.</span><span class="sxs-lookup"><span data-stu-id="5b3d6-109">The change can affect you if you've developed a .NET Core app with a type that derives from <xref:System.Windows.Forms.AccessibleObject> and accesses the `RuntimeIDFirstItem` field.</span></span> <span data-ttu-id="5b3d6-110">V takovém případě můžete definovat místní konstantu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="5b3d6-110">If this is the case, you can define a local constant as follows:</span></span>

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a><span data-ttu-id="5b3d6-111">Kategorie</span><span class="sxs-lookup"><span data-stu-id="5b3d6-111">Category</span></span>

<span data-ttu-id="5b3d6-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5b3d6-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5b3d6-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5b3d6-113">Affected APIs</span></span>

- <span data-ttu-id="5b3d6-114">Nedá se detekovat přes analýzu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="5b3d6-114">Not detectable via API analysis.</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
