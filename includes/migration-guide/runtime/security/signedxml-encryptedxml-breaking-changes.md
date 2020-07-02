---
ms.openlocfilehash: 8cc4f2ba2923774ef4e4e6861a89a7797ca988e1
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621079"
---
### <a name="signedxml-and-encryptedxml-breaking-changes"></a><span data-ttu-id="80276-101">SignedXml a EncryptedXml – průlomové změny</span><span class="sxs-lookup"><span data-stu-id="80276-101">SignedXml and EncryptedXml Breaking Changes</span></span>

#### <a name="details"></a><span data-ttu-id="80276-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="80276-102">Details</span></span>

<span data-ttu-id="80276-103">V .NET Framework 4.6.2 opravy zabezpečení v nástroji <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=fullName> a <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=fullName> vedou k různým chování za běhu.</span><span class="sxs-lookup"><span data-stu-id="80276-103">In .NET Framework 4.6.2, Security fixes in <xref:System.Security.Cryptography.Xml.SignedXml?displayProperty=fullName> and <xref:System.Security.Cryptography.Xml.EncryptedXml?displayProperty=fullName> lead to different run-time behaviors.</span></span> <span data-ttu-id="80276-104">Třeba</span><span class="sxs-lookup"><span data-stu-id="80276-104">For example,</span></span><ul><li><span data-ttu-id="80276-105">Pokud má dokument více elementů se stejným <code>id</code> atributem a signatura cílí na jeden z těchto prvků jako kořen podpisu, dokument bude nyní považován za neplatný.</span><span class="sxs-lookup"><span data-stu-id="80276-105">If a document has multiple elements with the same <code>id</code> attribute and a signature targets one of those elements as the root of the signature, the document will now be considered invalid.</span></span></li><li><span data-ttu-id="80276-106">Dokumenty, které používají nekanonické transformační algoritmy XPath v odkazech, jsou nyní považovány za neplatné.</span><span class="sxs-lookup"><span data-stu-id="80276-106">Documents using non-canonical XPath transform algorithms in references are now considered invalid.</span></span></li><li><span data-ttu-id="80276-107">Dokumenty, které používají nekanonické transformační algoritmy XSLT v odkazech, nyní považují za neplatné.</span><span class="sxs-lookup"><span data-stu-id="80276-107">Documents using non-canonical XSLT transform algorithms in references are now consider invalid.</span></span></li><li><span data-ttu-id="80276-108">Žádný program, který používá odpojené podpisy externích prostředků, to nebude moci udělat.</span><span class="sxs-lookup"><span data-stu-id="80276-108">Any program making use of external resource detached signatures will be unable to do so.</span></span></li></ul>

#### <a name="suggestion"></a><span data-ttu-id="80276-109">Návrh</span><span class="sxs-lookup"><span data-stu-id="80276-109">Suggestion</span></span>

<span data-ttu-id="80276-110">Vývojáři mohou chtít zkontrolovat použití <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> a a <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> také typy odvozené od <xref:System.Security.Cryptography.Xml.Transform> příjemce dokumentu nemusí být schopni je zpracovat.</span><span class="sxs-lookup"><span data-stu-id="80276-110">Developers might want to review the usage of <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform> and <xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform>, as well as types derived from <xref:System.Security.Cryptography.Xml.Transform> since a document receiver may not be able to process it.</span></span>

| <span data-ttu-id="80276-111">Name</span><span class="sxs-lookup"><span data-stu-id="80276-111">Name</span></span>    | <span data-ttu-id="80276-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="80276-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="80276-113">Rozsah</span><span class="sxs-lookup"><span data-stu-id="80276-113">Scope</span></span>   |<span data-ttu-id="80276-114">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="80276-114">Minor</span></span>|
|<span data-ttu-id="80276-115">Verze</span><span class="sxs-lookup"><span data-stu-id="80276-115">Version</span></span>|<span data-ttu-id="80276-116">4.6.2</span><span class="sxs-lookup"><span data-stu-id="80276-116">4.6.2</span></span>|
|<span data-ttu-id="80276-117">Typ</span><span class="sxs-lookup"><span data-stu-id="80276-117">Type</span></span>|<span data-ttu-id="80276-118">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="80276-118">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="80276-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="80276-119">Affected APIs</span></span>

-<xref:System.Security.Cryptography.Xml.Transform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXPathTransform?displayProperty=nameWithType></li><li><xref:System.Security.Cryptography.Xml.XmlDsigXsltTransform?displayProperty=nameWithType></li></ul>|
