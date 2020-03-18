---
ms.openlocfilehash: d48ced9d0201a33f9149aba155ddd3d8bc04c93f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74643954"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a><span data-ttu-id="de3d7-101">Serializovatelný atribut odebraný z některých typů formulářů systému Windows</span><span class="sxs-lookup"><span data-stu-id="de3d7-101">SerializableAttribute removed from some Windows Forms types</span></span>

<span data-ttu-id="de3d7-102">Byl <xref:System.SerializableAttribute> odebrán z některých tříd windows forms, které nemají žádné známé scénáře binární serializace.</span><span class="sxs-lookup"><span data-stu-id="de3d7-102">The <xref:System.SerializableAttribute> has been removed from some Windows Forms classes that have no known binary serialization scenarios.</span></span>

#### <a name="change-description"></a><span data-ttu-id="de3d7-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="de3d7-103">Change description</span></span>

<span data-ttu-id="de3d7-104">Následující typy jsou označeny rozhraním <xref:System.SerializableAttribute> in .NET Framework, ale atribut byl odebrán v rozhraní .NET Core:</span><span class="sxs-lookup"><span data-stu-id="de3d7-104">The following types are decorated with the <xref:System.SerializableAttribute> in .NET Framework, but the attribute has been removed in .NET Core:</span></span>

- `System.InvariantComparer`
- <xref:System.ComponentModel.Design.ExceptionCollection?displayProperty=nameWithType>
- <xref:System.ComponentModel.Design.Serialization.CodeDomSerializerException?displayProperty=nameWithType>
- `System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService.CodeDomSerializationStore`
- <xref:System.Drawing.Design.ToolboxItem?displayProperty=nameWithType>
- `System.Resources.ResXNullRef`
- `System.Resources.ResXDataNode`
- `System.Resources.ResXFileRef`
- <xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>
- `System.Windows.Forms.NativeMethods.MSOCRINFOSTRUCT`
- `System.Windows.Forms.NativeMethods.MSG`

<span data-ttu-id="de3d7-105">Historicky měl tento serializační mechanismus vážné obavy o údržbu a zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="de3d7-105">Historically, this serialization mechanism has had serious maintenance and security concerns.</span></span> <span data-ttu-id="de3d7-106">Udržování `SerializableAttribute` na typy znamená, že tyto typy musí být testovány pro změny serializace verze k verzi a potenciálně změny serializace architektury na architekturu.</span><span class="sxs-lookup"><span data-stu-id="de3d7-106">Maintaining `SerializableAttribute` on types means those types must be tested for version-to-version serialization changes and potentially framework-to-framework serialization changes.</span></span> <span data-ttu-id="de3d7-107">To ztěžuje vývoj těchto typů a může být nákladné udržovat.</span><span class="sxs-lookup"><span data-stu-id="de3d7-107">This makes it harder to evolve those types and can be costly to maintain.</span></span> <span data-ttu-id="de3d7-108">Tyto typy nemají žádné známé scénáře binární serializace, což minimalizuje dopad odebrání atributu.</span><span class="sxs-lookup"><span data-stu-id="de3d7-108">These types have no known binary serialization scenarios, which minimizes the impact of removing the attribute.</span></span>

<span data-ttu-id="de3d7-109">Další informace naleznete [v tématu Binary serializace](~/docs/standard/serialization/binary-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="de3d7-109">For more information, see [Binary serialization](~/docs/standard/serialization/binary-serialization.md).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="de3d7-110">Zavedená verze</span><span class="sxs-lookup"><span data-stu-id="de3d7-110">Version introduced</span></span>

<span data-ttu-id="de3d7-111">3.0 Náhled 9</span><span class="sxs-lookup"><span data-stu-id="de3d7-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="de3d7-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="de3d7-112">Recommended action</span></span>

<span data-ttu-id="de3d7-113">Aktualizujte libovolný kód, který může záviset na těchto typech, které jsou označeny jako serializovatelné.</span><span class="sxs-lookup"><span data-stu-id="de3d7-113">Update any code that may depend on these types being marked as serializable.</span></span>

#### <a name="category"></a><span data-ttu-id="de3d7-114">Kategorie</span><span class="sxs-lookup"><span data-stu-id="de3d7-114">Category</span></span>

<span data-ttu-id="de3d7-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="de3d7-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="de3d7-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="de3d7-116">Affected APIs</span></span>

- <span data-ttu-id="de3d7-117">Žádný</span><span class="sxs-lookup"><span data-stu-id="de3d7-117">None</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
