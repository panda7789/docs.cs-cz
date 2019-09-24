---
ms.openlocfilehash: d48ced9d0201a33f9149aba155ddd3d8bc04c93f
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217043"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a><span data-ttu-id="b4131-101">SerializableAttribute byl odebrán z některých typů model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b4131-101">SerializableAttribute removed from some Windows Forms types</span></span>

<span data-ttu-id="b4131-102"><xref:System.SerializableAttribute> Byl odebrán z některých tříd model Windows Forms, které nemají žádné známé scénáře binární serializace.</span><span class="sxs-lookup"><span data-stu-id="b4131-102">The <xref:System.SerializableAttribute> has been removed from some Windows Forms classes that have no known binary serialization scenarios.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b4131-103">Změnit popis</span><span class="sxs-lookup"><span data-stu-id="b4131-103">Change description</span></span>

<span data-ttu-id="b4131-104">Následující typy jsou upraveny pomocí <xref:System.SerializableAttribute> .NET Framework, ale atribut byl odebrán v rozhraní .NET Core:</span><span class="sxs-lookup"><span data-stu-id="b4131-104">The following types are decorated with the <xref:System.SerializableAttribute> in .NET Framework, but the attribute has been removed in .NET Core:</span></span>

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

<span data-ttu-id="b4131-105">V minulosti měl tento mechanismus serializace závažné problémy s údržbou a zabezpečením.</span><span class="sxs-lookup"><span data-stu-id="b4131-105">Historically, this serialization mechanism has had serious maintenance and security concerns.</span></span> <span data-ttu-id="b4131-106">Údržba `SerializableAttribute` na typech znamená, že tyto typy musí být testovány pro změny serializace verze na verzi a potenciálně změny serializace architektury rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b4131-106">Maintaining `SerializableAttribute` on types means those types must be tested for version-to-version serialization changes and potentially framework-to-framework serialization changes.</span></span> <span data-ttu-id="b4131-107">Díky tomu je to obtížnější je rozvíjet tyto typy a může být náročné na údržbu.</span><span class="sxs-lookup"><span data-stu-id="b4131-107">This makes it harder to evolve those types and can be costly to maintain.</span></span> <span data-ttu-id="b4131-108">Tyto typy nemají žádné známé scénáře binární serializace, což minimalizuje dopad odebrání atributu.</span><span class="sxs-lookup"><span data-stu-id="b4131-108">These types have no known binary serialization scenarios, which minimizes the impact of removing the attribute.</span></span>

<span data-ttu-id="b4131-109">Další informace naleznete v tématu [binární serializace](~/docs/standard/serialization/binary-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="b4131-109">For more information, see [Binary serialization](~/docs/standard/serialization/binary-serialization.md).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b4131-110">Představená verze</span><span class="sxs-lookup"><span data-stu-id="b4131-110">Version introduced</span></span>

<span data-ttu-id="b4131-111">3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="b4131-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b4131-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="b4131-112">Recommended action</span></span>

<span data-ttu-id="b4131-113">Aktualizujte jakýkoli kód, který může záviset na těchto typech označených jako serializovatelný.</span><span class="sxs-lookup"><span data-stu-id="b4131-113">Update any code that may depend on these types being marked as serializable.</span></span>

#### <a name="category"></a><span data-ttu-id="b4131-114">Kategorie</span><span class="sxs-lookup"><span data-stu-id="b4131-114">Category</span></span>

<span data-ttu-id="b4131-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b4131-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b4131-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b4131-116">Affected APIs</span></span>

- <span data-ttu-id="b4131-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="b4131-117">None</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
