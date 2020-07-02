---
ms.openlocfilehash: 9b734fe960165b6d4b97b861cb3e8f31979f25c5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621085"
---
### <a name="remove-ssl3-from-the-wcf-transportdefaults"></a><span data-ttu-id="ca1f1-101">Odebrání SSL3 z TransportDefaults WCF</span><span class="sxs-lookup"><span data-stu-id="ca1f1-101">Remove Ssl3 from the WCF TransportDefaults</span></span>

#### <a name="details"></a><span data-ttu-id="ca1f1-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ca1f1-102">Details</span></span>

<span data-ttu-id="ca1f1-103">Pokud používáte NetTcp se zabezpečením přenosu a typem přihlašovacích údajů certifikátu, protokol SSL 3 už není výchozím protokolem používaným pro vyjednávání zabezpečeného připojení.</span><span class="sxs-lookup"><span data-stu-id="ca1f1-103">When using NetTcp with transport security and a credential type of certificate, the SSL 3 protocol is no longer a default protocol used for negotiating a secure connection.</span></span> <span data-ttu-id="ca1f1-104">Ve většině případů by nemělo dojít k žádným dopadům na stávající aplikace, protože protokol TLS 1,0 byl vždycky zahrnutý do seznamu protokolů pro NetTcp.</span><span class="sxs-lookup"><span data-stu-id="ca1f1-104">In most cases there should be no impact to existing apps as TLS 1.0 has always been included in the protocol list for NetTcp.</span></span> <span data-ttu-id="ca1f1-105">Všichni existující klienti by měli být schopni vyjednat připojení pomocí aspoň TLS 1.0.</span><span class="sxs-lookup"><span data-stu-id="ca1f1-105">All existing clients should be able to negotiate a connection using at least TLS1.0.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ca1f1-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="ca1f1-106">Suggestion</span></span>

<span data-ttu-id="ca1f1-107">Pokud se vyžaduje SSL3, použijte jeden z následujících konfiguračních mechanismů a přidejte SSL3 do seznamu sjednaných protokolů.</span><span class="sxs-lookup"><span data-stu-id="ca1f1-107">If Ssl3 is required, use one of the following configuration mechanisms to add Ssl3 to the list of negotiated protocols.</span></span><ul><li><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols></li><li>[<](~/docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)</li><li><span data-ttu-id="ca1f1-108">[ &lt; &gt; oddíl sslStreamSecurity v &lt; CustomBinding &gt; ] ~/docs/Framework/Configure-Apps/File-Schema/WCF/sslStreamSecurity.MD)</span><span class="sxs-lookup"><span data-stu-id="ca1f1-108">[&lt;sslStreamSecurity&gt; section of &lt;customBinding&gt;]~/docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</span></span></li></ul>

| <span data-ttu-id="ca1f1-109">Name</span><span class="sxs-lookup"><span data-stu-id="ca1f1-109">Name</span></span>    | <span data-ttu-id="ca1f1-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ca1f1-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ca1f1-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="ca1f1-111">Scope</span></span>   |<span data-ttu-id="ca1f1-112">Edge</span><span class="sxs-lookup"><span data-stu-id="ca1f1-112">Edge</span></span>|
|<span data-ttu-id="ca1f1-113">Verze</span><span class="sxs-lookup"><span data-stu-id="ca1f1-113">Version</span></span>|<span data-ttu-id="ca1f1-114">4.6.2</span><span class="sxs-lookup"><span data-stu-id="ca1f1-114">4.6.2</span></span>|
|<span data-ttu-id="ca1f1-115">Typ</span><span class="sxs-lookup"><span data-stu-id="ca1f1-115">Type</span></span>|<span data-ttu-id="ca1f1-116">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="ca1f1-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ca1f1-117">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="ca1f1-117">Affected APIs</span></span>

-<xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols?displayProperty=nameWithType></li><li><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols?displayProperty=nameWithType></li></ul>|
