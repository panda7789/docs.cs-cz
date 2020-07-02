---
ms.openlocfilehash: 5c27e8acdf30533036546ba4cca9e06877bde362
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620117"
---
### <a name="xslt-style-sheet-exception-message-changed"></a><span data-ttu-id="2885d-101">Došlo ke změně zprávy o výjimce šablony stylů XSLT.</span><span class="sxs-lookup"><span data-stu-id="2885d-101">XSLT style sheet exception message changed</span></span>

#### <a name="details"></a><span data-ttu-id="2885d-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="2885d-102">Details</span></span>

<span data-ttu-id="2885d-103">V .NET Framework 4,5 text chybové zprávy, pokud je soubor XSLT příliš složitý, je &quot; Šablona stylů příliš složitá. &quot; V předchozích verzích byla chybová zpráva &quot; chybou kompilace XSLT. &quot; Kód aplikace, který závisí na textu chybové zprávy, již nebude fungovat.</span><span class="sxs-lookup"><span data-stu-id="2885d-103">In the .NET Framework 4.5, the text of the error message when an XSLT file is too complex is &quot;The style sheet is too complex.&quot; In previous versions, the error message was &quot;XSLT compile error.&quot; Application code that depends on the text of the error message will no longer work.</span></span> <span data-ttu-id="2885d-104">Typy výjimek však zůstanou stejné, takže tato změna by neměla mít žádný skutečný dopad.</span><span class="sxs-lookup"><span data-stu-id="2885d-104">However, the exception types remain the same, so this change should have no real impact.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="2885d-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="2885d-105">Suggestion</span></span>

<span data-ttu-id="2885d-106">Aktualizujte jakýkoli kód aplikace v závislosti na zprávě výjimky z tohoto chybové podmínky, abyste očekávali novou zprávu, nebo (ještě lepší) aktualizovat kód tak, aby byl závislý jenom na typu výjimky ( <xref:System.Xml.Xsl.XsltException?displayProperty=fullName> ), který se nezměnil.</span><span class="sxs-lookup"><span data-stu-id="2885d-106">Update any app code depending on the exception message from this error condition to expect the new message, or (even better) update the code to depend only on the exception type (<xref:System.Xml.Xsl.XsltException?displayProperty=fullName>), which has not changed.</span></span>

| <span data-ttu-id="2885d-107">Name</span><span class="sxs-lookup"><span data-stu-id="2885d-107">Name</span></span>    | <span data-ttu-id="2885d-108">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2885d-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="2885d-109">Rozsah</span><span class="sxs-lookup"><span data-stu-id="2885d-109">Scope</span></span>   |<span data-ttu-id="2885d-110">Edge</span><span class="sxs-lookup"><span data-stu-id="2885d-110">Edge</span></span>|
|<span data-ttu-id="2885d-111">Verze</span><span class="sxs-lookup"><span data-stu-id="2885d-111">Version</span></span>|<span data-ttu-id="2885d-112">4.5</span><span class="sxs-lookup"><span data-stu-id="2885d-112">4.5</span></span>|
|<span data-ttu-id="2885d-113">Typ</span><span class="sxs-lookup"><span data-stu-id="2885d-113">Type</span></span>|<span data-ttu-id="2885d-114">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="2885d-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2885d-115">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="2885d-115">Affected APIs</span></span>

-<xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Type)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Reflection.MethodInfo,System.Byte[],System.Type[])?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.String,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XmlReader,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li><li><xref:System.Xml.Xsl.XslCompiledTransform.Load(System.Xml.XPath.IXPathNavigable,System.Xml.Xsl.XsltSettings,System.Xml.XmlResolver)?displayProperty=nameWithType></li></ul>|
