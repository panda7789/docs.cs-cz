---
ms.openlocfilehash: 4fb1ffed97a5b7f906bed13a69f1e71563d11dae
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556151"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a><span data-ttu-id="02549-101">SerializableAttribute byl odebrán z některých typů model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="02549-101">SerializableAttribute removed from some Windows Forms types</span></span>

<span data-ttu-id="02549-102">Byl <xref:System.SerializableAttribute> odebrán z některých tříd model Windows Forms, které nemají žádné známé scénáře binární serializace.</span><span class="sxs-lookup"><span data-stu-id="02549-102">The <xref:System.SerializableAttribute> has been removed from some Windows Forms classes that have no known binary serialization scenarios.</span></span>

#### <a name="change-description"></a><span data-ttu-id="02549-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="02549-103">Change description</span></span>

<span data-ttu-id="02549-104">Následující typy jsou upraveny pomocí <xref:System.SerializableAttribute> .NET Framework, ale atribut byl odebrán v rozhraní .NET Core:</span><span class="sxs-lookup"><span data-stu-id="02549-104">The following types are decorated with the <xref:System.SerializableAttribute> in .NET Framework, but the attribute has been removed in .NET Core:</span></span>

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

<span data-ttu-id="02549-105">V minulosti měl tento mechanismus serializace závažné problémy s údržbou a zabezpečením.</span><span class="sxs-lookup"><span data-stu-id="02549-105">Historically, this serialization mechanism has had serious maintenance and security concerns.</span></span> <span data-ttu-id="02549-106">Údržba `SerializableAttribute` na typech znamená, že tyto typy musí být testovány pro změny serializace verze na verzi a potenciálně změny serializace architektury rozhraní.</span><span class="sxs-lookup"><span data-stu-id="02549-106">Maintaining `SerializableAttribute` on types means those types must be tested for version-to-version serialization changes and potentially framework-to-framework serialization changes.</span></span> <span data-ttu-id="02549-107">Díky tomu je to obtížnější je rozvíjet tyto typy a může být náročné na údržbu.</span><span class="sxs-lookup"><span data-stu-id="02549-107">This makes it harder to evolve those types and can be costly to maintain.</span></span> <span data-ttu-id="02549-108">Tyto typy nemají žádné známé scénáře binární serializace, což minimalizuje dopad odebrání atributu.</span><span class="sxs-lookup"><span data-stu-id="02549-108">These types have no known binary serialization scenarios, which minimizes the impact of removing the attribute.</span></span>

<span data-ttu-id="02549-109">Další informace naleznete v tématu [binární serializace](~/docs/standard/serialization/binary-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="02549-109">For more information, see [Binary serialization](~/docs/standard/serialization/binary-serialization.md).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="02549-110">Představená verze</span><span class="sxs-lookup"><span data-stu-id="02549-110">Version introduced</span></span>

<span data-ttu-id="02549-111">3.0</span><span class="sxs-lookup"><span data-stu-id="02549-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="02549-112">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="02549-112">Recommended action</span></span>

<span data-ttu-id="02549-113">Aktualizujte jakýkoli kód, který může záviset na těchto typech označených jako serializovatelný.</span><span class="sxs-lookup"><span data-stu-id="02549-113">Update any code that may depend on these types being marked as serializable.</span></span>

#### <a name="category"></a><span data-ttu-id="02549-114">Kategorie</span><span class="sxs-lookup"><span data-stu-id="02549-114">Category</span></span>

<span data-ttu-id="02549-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="02549-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="02549-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="02549-116">Affected APIs</span></span>

- <span data-ttu-id="02549-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="02549-117">None</span></span>

<!--

#### Affected APIs

- Not detectable via API analysis

-->
