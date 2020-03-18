---
ms.openlocfilehash: 5bbbf9075683b0f124e126b661b4ab85011e6c2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74644045"
---
### <a name="change-of-access-for-accessibleobjectruntimeidfirstitem"></a><span data-ttu-id="40409-101">Změna přístupu pro AccessibleObject.RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="40409-101">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>

<span data-ttu-id="40409-102">Počínaje rozhraním .NET Core 3.0 `AccessibleObject.RuntimeIDFirstItem` RC1 `protected` se `internal`přístupnost nástroje změnila z na .</span><span class="sxs-lookup"><span data-stu-id="40409-102">Starting in .NET Core 3.0 RC1, the accessibility of `AccessibleObject.RuntimeIDFirstItem` has changed from `protected` to `internal`.</span></span>

#### <a name="change-description"></a><span data-ttu-id="40409-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="40409-103">Change description</span></span>

<span data-ttu-id="40409-104">Počínaje rozhraním .NET Core 3.0 `protected`Preview 4 bylo `AccessibleObject.RuntimeIDFirstItem` pole .</span><span class="sxs-lookup"><span data-stu-id="40409-104">Starting with .NET Core 3.0 Preview 4, the `AccessibleObject.RuntimeIDFirstItem` field was `protected`.</span></span> <span data-ttu-id="40409-105">Počínaje rozhraním .NET Core 3.0 RC1 `internal` se změnil z `protected` na zarovnat s usnadněním přístupu pole v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="40409-105">Starting with .NET Core 3.0 RC1, it has changed from `protected` to `internal` to align with the accessibility of the field in the .NET Framework.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="40409-106">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="40409-106">Version introduced</span></span>

<span data-ttu-id="40409-107">3.0 RC1</span><span class="sxs-lookup"><span data-stu-id="40409-107">3.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="40409-108">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="40409-108">Recommended action</span></span>

<span data-ttu-id="40409-109">Změna může ovlivnit vás, pokud jste vyvinuli aplikaci .NET Core <xref:System.Windows.Forms.AccessibleObject> s typem, který je odvozen od pole a přistupuje k němu. `RuntimeIDFirstItem`</span><span class="sxs-lookup"><span data-stu-id="40409-109">The change can affect you if you've developed a .NET Core app with a type that derives from <xref:System.Windows.Forms.AccessibleObject> and accesses the `RuntimeIDFirstItem` field.</span></span> <span data-ttu-id="40409-110">Pokud se jedná o tento případ, můžete definovat místní konstantu takto:</span><span class="sxs-lookup"><span data-stu-id="40409-110">If this is the case, you can define a local constant as follows:</span></span>

```csharp
const int RuntimeIDFirstItem = 0x2a;
```

#### <a name="category"></a><span data-ttu-id="40409-111">Kategorie</span><span class="sxs-lookup"><span data-stu-id="40409-111">Category</span></span>

<span data-ttu-id="40409-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="40409-112">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="40409-113">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="40409-113">Affected APIs</span></span>

- <span data-ttu-id="40409-114">Nelze zjistit pomocí analýzy rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="40409-114">Not detectable via API analysis.</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis.

-->
