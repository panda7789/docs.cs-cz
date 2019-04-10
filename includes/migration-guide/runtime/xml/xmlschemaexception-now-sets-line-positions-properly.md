---
ms.openlocfilehash: a5b3e325c13d2f56532ebc6ebb5c259d565a4952
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235366"
---
### <a name="xmlschemaexception-now-sets-line-positions-properly"></a><span data-ttu-id="5df57-101">Xmlschemaexception – správně teď nastavuje pozice řádků</span><span class="sxs-lookup"><span data-stu-id="5df57-101">XmlSchemaException now sets line positions properly</span></span>

|   |   |
|---|---|
|<span data-ttu-id="5df57-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="5df57-102">Details</span></span>|<span data-ttu-id="5df57-103">Pokud <xref:System.Xml.Linq.LoadOptions.SetLineInfo> hodnota se předá metodě načíst a dojde k chybě ověření, <xref:System.Xml.Schema.XmlSchemaException.LineNumber> a <xref:System.Xml.Schema.XmlSchemaException.LinePosition> vlastnosti nyní obsahují informace řádku.</span><span class="sxs-lookup"><span data-stu-id="5df57-103">If the <xref:System.Xml.Linq.LoadOptions.SetLineInfo> value is passed to the Load method and a validation error occurs, the <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> properties now contain line information.</span></span>|
|<span data-ttu-id="5df57-104">Doporučení</span><span class="sxs-lookup"><span data-stu-id="5df57-104">Suggestion</span></span>|<span data-ttu-id="5df57-105">Kód zpracování výjimek, který předpokládá <xref:System.Xml.Schema.XmlSchemaException.LineNumber> a <xref:System.Xml.Schema.XmlSchemaException.LinePosition> nebude sada by měl aktualizovat, protože tyto vlastnosti budou nyní nastavit správně při použití SetLineInfo při načítání XML.</span><span class="sxs-lookup"><span data-stu-id="5df57-105">Exception-handling code that assumes <xref:System.Xml.Schema.XmlSchemaException.LineNumber> and <xref:System.Xml.Schema.XmlSchemaException.LinePosition> will not be set should be updated since these properties will now be set properly when SetLineInfo is used while loading XML.</span></span>|
|<span data-ttu-id="5df57-106">Rozsah</span><span class="sxs-lookup"><span data-stu-id="5df57-106">Scope</span></span>|<span data-ttu-id="5df57-107">Edge</span><span class="sxs-lookup"><span data-stu-id="5df57-107">Edge</span></span>|
|<span data-ttu-id="5df57-108">Version</span><span class="sxs-lookup"><span data-stu-id="5df57-108">Version</span></span>|<span data-ttu-id="5df57-109">4.5</span><span class="sxs-lookup"><span data-stu-id="5df57-109">4.5</span></span>|
|<span data-ttu-id="5df57-110">Type</span><span class="sxs-lookup"><span data-stu-id="5df57-110">Type</span></span>|<span data-ttu-id="5df57-111">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="5df57-111">Runtime</span></span>|
|<span data-ttu-id="5df57-112">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5df57-112">Affected APIs</span></span>|<ul><li><xref:System.Xml.Linq.LoadOptions.SetLineInfo?displayProperty=nameWithType></li></ul>|
