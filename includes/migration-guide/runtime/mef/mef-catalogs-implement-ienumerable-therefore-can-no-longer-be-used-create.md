---
ms.openlocfilehash: 598df2121b480d411dac9c5571772a4a8d22b5ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620035"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a><span data-ttu-id="e57c5-101">Katalogy MEF implementují rozhraní IEnumerable a proto se už nedají použít k vytvoření serializátoru.</span><span class="sxs-lookup"><span data-stu-id="e57c5-101">MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer</span></span>

#### <a name="details"></a><span data-ttu-id="e57c5-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e57c5-102">Details</span></span>

<span data-ttu-id="e57c5-103">Počínaje .NET Framework 4,5, katalogy MEF implementují rozhraní IEnumerable, a proto je nelze nadále používat k vytvoření serializátoru ( <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> objektu).</span><span class="sxs-lookup"><span data-stu-id="e57c5-103">Starting with the .NET Framework 4.5, MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> object).</span></span> <span data-ttu-id="e57c5-104">Při pokusu o serializaci katalogu MEF vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="e57c5-104">Trying to serialize a MEF catalog throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="e57c5-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="e57c5-105">Suggestion</span></span>

<span data-ttu-id="e57c5-106">Rozhraní MEF již nelze použít k vytvoření serializátoru.</span><span class="sxs-lookup"><span data-stu-id="e57c5-106">Can no longer use MEF to create a serializer</span></span>

| <span data-ttu-id="e57c5-107">Name</span><span class="sxs-lookup"><span data-stu-id="e57c5-107">Name</span></span>    | <span data-ttu-id="e57c5-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="e57c5-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="e57c5-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="e57c5-109">Scope</span></span>   |<span data-ttu-id="e57c5-110">Hlavní</span><span class="sxs-lookup"><span data-stu-id="e57c5-110">Major</span></span>|
|<span data-ttu-id="e57c5-111">Verze</span><span class="sxs-lookup"><span data-stu-id="e57c5-111">Version</span></span>|<span data-ttu-id="e57c5-112">4.5</span><span class="sxs-lookup"><span data-stu-id="e57c5-112">4.5</span></span>|
|<span data-ttu-id="e57c5-113">Typ</span><span class="sxs-lookup"><span data-stu-id="e57c5-113">Type</span></span>|<span data-ttu-id="e57c5-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="e57c5-114">Runtime</span></span>|
