---
ms.openlocfilehash: 1ea2d70a7cfe04cc4c4b9b58ea6bb6fa0226b245
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721281"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a><span data-ttu-id="e55e8-101">Změna přístupu pro třída AccessibleObject. RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="e55e8-101">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>

<span data-ttu-id="e55e8-102">Od verze .NET Core 3,0 RC1 se přístupnost pro `AccessibleObject.RuntimeIDFirstItem` změnila z `protected` na `internal` .</span><span class="sxs-lookup"><span data-stu-id="e55e8-102">Starting in .NET Core 3.0 RC1, the accessibility of `AccessibleObject.RuntimeIDFirstItem` has changed from `protected` to `internal`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="e55e8-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="e55e8-103">Change description</span></span>

<span data-ttu-id="e55e8-104">Od verze .NET Core 3,0 Preview 4 `AccessibleObject.RuntimeIDFirstItem` bylo pole `protected` .</span><span class="sxs-lookup"><span data-stu-id="e55e8-104">Starting with .NET Core 3.0 Preview 4, the `AccessibleObject.RuntimeIDFirstItem` field was `protected`.</span></span> <span data-ttu-id="e55e8-105">Od verze .NET Core 3,0 RC1 se změnila z verze `protected` na, `internal` aby byla zarovnaná s přístupností pole v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e55e8-105">Starting with .NET Core 3.0 RC1, it has changed from `protected` to `internal` to align with the accessibility of the field in the .NET Framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e55e8-106">Představená verze</span><span class="sxs-lookup"><span data-stu-id="e55e8-106">Version introduced</span></span>

<span data-ttu-id="e55e8-107">3,0 RC1</span><span class="sxs-lookup"><span data-stu-id="e55e8-107">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e55e8-108">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="e55e8-108">Recommended action</span></span>

<span data-ttu-id="e55e8-109">Tato změna může mít vliv na to, zda jste vytvořili aplikaci .NET Core s typem, který je odvozen z <xref:System.Windows.Forms.AccessibleObject> a přistupuje k `RuntimeIDFirstItem` poli.</span><span class="sxs-lookup"><span data-stu-id="e55e8-109">The change can affect you if you've developed a .NET Core app with a type that derives from <xref:System.Windows.Forms.AccessibleObject> and accesses the `RuntimeIDFirstItem` field.</span></span> <span data-ttu-id="e55e8-110">V takovém případě můžete definovat místní konstantu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e55e8-110">If this is the case, you can define a local constant as follows:</span></span>

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a><span data-ttu-id="e55e8-111">Kategorie</span><span class="sxs-lookup"><span data-stu-id="e55e8-111">Category</span></span>

<span data-ttu-id="e55e8-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e55e8-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e55e8-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="e55e8-113">Affected APIs</span></span>

- <span data-ttu-id="e55e8-114">Nedá se detekovat přes analýzu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="e55e8-114">Not detectable via API analysis.</span></span>

<!-- 

#### Affected APIs

- Not detectable via API analysis.

-->
