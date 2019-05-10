---
title: 'Omezení rizik: Protokoly TLS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b21dc73454b96d3a192b47eb439bebf588059c24
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599625"
---
# <a name="mitigation-tls-protocols"></a><span data-ttu-id="6241b-102">Omezení rizik: Protokoly TLS</span><span class="sxs-lookup"><span data-stu-id="6241b-102">Mitigation: TLS Protocols</span></span>
<span data-ttu-id="6241b-103">Od verze rozhraní .NET Framework 4.6 <xref:System.Net.ServicePointManager?displayProperty=nameWithType> a <xref:System.Net.Security.SslStream?displayProperty=nameWithType> třídy mohou používat jednu z těchto tří protokolů: Protokol TLS 1.0, Tls1.1 nebo Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="6241b-103">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager?displayProperty=nameWithType> and <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes are allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="6241b-104">SSL3.0 protokolu a šifer RC4 nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="6241b-104">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="6241b-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="6241b-105">Impact</span></span>  
 <span data-ttu-id="6241b-106">Tato změna ovlivní:</span><span class="sxs-lookup"><span data-stu-id="6241b-106">This change affects:</span></span>  
  
- <span data-ttu-id="6241b-107">Jakékoli aplikaci, která používá protokol SSL na serveru HTTPS nebo server websocket pomocí kteréhokoli z následujících typů: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, a <xref:System.Net.Security.SslStream>.</span><span class="sxs-lookup"><span data-stu-id="6241b-107">Any app that uses SSL to talk to an HTTPS server or a socket server using any of the following types: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, and <xref:System.Net.Security.SslStream>.</span></span>  
  
- <span data-ttu-id="6241b-108">Libovolné aplikace na straně serveru, který nelze upgradovat pro podporu protokolu Tls 1.2, protokol TLS 1.0 nebo Tls1.1...</span><span class="sxs-lookup"><span data-stu-id="6241b-108">Any server-side app that cannot be upgraded to support Tls1.0, Tls1.1, or Tls 1.2..</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="6241b-109">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="6241b-109">Mitigation</span></span>  
 <span data-ttu-id="6241b-110">Doporučené omezení rizik je upgrade aplikace straně serveru pro protokol TLS 1.0, Tls1.1 nebo Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="6241b-110">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="6241b-111">Pokud to není proveditelné, nebo pokud jsou přerušená, klientské aplikace <xref:System.AppContext> třídy lze tuto funkci v některém ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="6241b-111">If this is not feasible, or if client apps are broken, the <xref:System.AppContext> class can be used to opt out of this feature in either of two ways:</span></span>  
  
- <span data-ttu-id="6241b-112">Programově pomocí fragmentu kódu, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="6241b-112">Programmatically, by using a code snippet like the following:</span></span>  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <span data-ttu-id="6241b-113">Vzhledem k tomu, <xref:System.Net.ServicePointManager> objekt je inicializován pouze jednou, definuje tato nastavení kompatibility musí být první věc, kterou aplikace dělá.</span><span class="sxs-lookup"><span data-stu-id="6241b-113">Because the <xref:System.Net.ServicePointManager> object is initialized only once, defining these compatibility settings must be the first thing the application does.</span></span>  
  
- <span data-ttu-id="6241b-114">Přidejte následující řádek, který [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) části souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="6241b-114">By adding the following line to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 <span data-ttu-id="6241b-115">Všimněte si však, že přestanete používat výchozí chování se nedoporučuje, protože je méně zabezpečené aplikace.</span><span class="sxs-lookup"><span data-stu-id="6241b-115">Note, however, that opting out of the default behavior is not recommended, since it makes the application less secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6241b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6241b-116">See also</span></span>

- [<span data-ttu-id="6241b-117">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="6241b-117">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
