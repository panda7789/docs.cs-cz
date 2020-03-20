---
title: 'Omezení rizik: Protokoly TLS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
ms.openlocfilehash: 45225d73ac60564d3e22c73270faab6b4e04d697
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457836"
---
# <a name="mitigation-tls-protocols"></a><span data-ttu-id="b96a5-102">Omezení rizik: Protokoly TLS</span><span class="sxs-lookup"><span data-stu-id="b96a5-102">Mitigation: TLS Protocols</span></span>
<span data-ttu-id="b96a5-103">Počínaje rozhraním .NET Framework 4.6 mohou třídy <xref:System.Net.ServicePointManager?displayProperty=nameWithType> a <xref:System.Net.Security.SslStream?displayProperty=nameWithType> používat jeden z následujících tří protokolů: Tls1.0, Tls1.1 nebo Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="b96a5-103">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager?displayProperty=nameWithType> and <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes are allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="b96a5-104">Protokol SSL3.0 a šifra RC4 nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="b96a5-104">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="b96a5-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="b96a5-105">Impact</span></span>  
 <span data-ttu-id="b96a5-106">Tato změna má vliv na:</span><span class="sxs-lookup"><span data-stu-id="b96a5-106">This change affects:</span></span>  
  
- <span data-ttu-id="b96a5-107">Libovolná aplikace, která používá protokol SSL k komunikaci se serverem <xref:System.Net.Http.HttpClient> <xref:System.Net.HttpWebRequest>HTTPS <xref:System.Net.FtpWebRequest> <xref:System.Net.Mail.SmtpClient>nebo soketovým serverem pomocí některého z následujících typů: , , , a <xref:System.Net.Security.SslStream>.</span><span class="sxs-lookup"><span data-stu-id="b96a5-107">Any app that uses SSL to talk to an HTTPS server or a socket server using any of the following types: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, and <xref:System.Net.Security.SslStream>.</span></span>  
  
- <span data-ttu-id="b96a5-108">Jakákoli aplikace na straně serveru, kterou nelze upgradovat na podporu Tls1.0, Tls1.1 nebo Tls 1.2..</span><span class="sxs-lookup"><span data-stu-id="b96a5-108">Any server-side app that cannot be upgraded to support Tls1.0, Tls1.1, or Tls 1.2..</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="b96a5-109">Omezení rizik</span><span class="sxs-lookup"><span data-stu-id="b96a5-109">Mitigation</span></span>  
 <span data-ttu-id="b96a5-110">Doporučené zmírnění je upgrade aplikace na straně sever na Tls1.0, Tls1.1 nebo Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="b96a5-110">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="b96a5-111">Pokud to není možné, nebo pokud klientské <xref:System.AppContext> aplikace jsou rozbité, třídy lze odhlásit z této funkce v jednom ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="b96a5-111">If this is not feasible, or if client apps are broken, the <xref:System.AppContext> class can be used to opt out of this feature in either of two ways:</span></span>  
  
- <span data-ttu-id="b96a5-112">Programově pomocí fragmentu kódu, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="b96a5-112">Programmatically, by using a code snippet like the following:</span></span>  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <span data-ttu-id="b96a5-113">Vzhledem <xref:System.Net.ServicePointManager> k tomu, že objekt je inicializován pouze jednou, definování těchto nastavení kompatibility musí být první věc, kterou aplikace provede.</span><span class="sxs-lookup"><span data-stu-id="b96a5-113">Because the <xref:System.Net.ServicePointManager> object is initialized only once, defining these compatibility settings must be the first thing the application does.</span></span>  
  
- <span data-ttu-id="b96a5-114">Přidáním následujícího řádku do sekce [ \<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="b96a5-114">By adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 <span data-ttu-id="b96a5-115">Všimněte si však, že odhlášení z výchozí chování se nedoporučuje, protože aplikace méně zabezpečené.</span><span class="sxs-lookup"><span data-stu-id="b96a5-115">Note, however, that opting out of the default behavior is not recommended, since it makes the application less secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b96a5-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="b96a5-116">See also</span></span>

- [<span data-ttu-id="b96a5-117">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="b96a5-117">Application compatibility</span></span>](application-compatibility.md)
