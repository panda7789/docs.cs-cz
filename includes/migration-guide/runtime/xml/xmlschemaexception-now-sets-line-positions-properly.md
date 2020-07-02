---
ms.openlocfilehash: c3e39e49747be709977d7fba3c39b59f5575c40d
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620110"
---
### <a name="xmlschemaexception-now-sets-line-positions-properly"></a><span data-ttu-id="eefec-101">XmlSchemaException – nyní nastavuje pozice řádků správně</span><span class="sxs-lookup"><span data-stu-id="eefec-101">XmlSchemaException now sets line positions properly</span></span>

#### <a name="details"></a><span data-ttu-id="eefec-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="eefec-102">Details</span></span>

<span data-ttu-id="eefec-103">Pokud <xref:System.Xml.Linq.LoadOptions.SetLineInfo> je hodnota předána metodě Load a dojde k chybě ověření, <xref:System.Xml.Schema.XmlSchemaException.LineNumber> <xref:System.Xml.Schema.XmlSchemaException.LinePosition> vlastnosti a nyní obsahují informace o řádku.</span><span class="sxs-lookup"><span data-stu-id="eefec-103">If the <xref:System.Xml.Linq.LoadOptions.SetLineInfo> value is passed to the Load method and a validation error occurs, the <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> properties now contain line information.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="eefec-104">Návrh</span><span class="sxs-lookup"><span data-stu-id="eefec-104">Suggestion</span></span>

<span data-ttu-id="eefec-105">Kód pro zpracování výjimek, který předpokládá <xref:System.Xml.Schema.XmlSchemaException.LineNumber> a <xref:System.Xml.Schema.XmlSchemaException.LinePosition> nebude nastaven, by měl být aktualizován, protože tyto vlastnosti budou nyní nastaveny správně, pokud se při načítání XML používá SetLineInfo.</span><span class="sxs-lookup"><span data-stu-id="eefec-105">Exception-handling code that assumes <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> will not be set should be updated since these properties will now be set properly when SetLineInfo is used while loading XML.</span></span>

| <span data-ttu-id="eefec-106">Name</span><span class="sxs-lookup"><span data-stu-id="eefec-106">Name</span></span>    | <span data-ttu-id="eefec-107">Hodnota</span><span class="sxs-lookup"><span data-stu-id="eefec-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="eefec-108">Rozsah</span><span class="sxs-lookup"><span data-stu-id="eefec-108">Scope</span></span>   |<span data-ttu-id="eefec-109">Edge</span><span class="sxs-lookup"><span data-stu-id="eefec-109">Edge</span></span>|
|<span data-ttu-id="eefec-110">Verze</span><span class="sxs-lookup"><span data-stu-id="eefec-110">Version</span></span>|<span data-ttu-id="eefec-111">4.5</span><span class="sxs-lookup"><span data-stu-id="eefec-111">4.5</span></span>|
|<span data-ttu-id="eefec-112">Typ</span><span class="sxs-lookup"><span data-stu-id="eefec-112">Type</span></span>|<span data-ttu-id="eefec-113">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="eefec-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="eefec-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="eefec-114">Affected APIs</span></span>

-<xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|
