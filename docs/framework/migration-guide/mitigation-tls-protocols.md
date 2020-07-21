---
title: 'Omezení rizik: Protokoly TLS'
description: Přečtěte si o dopadu a zmírnění omezení pro změny protokolu TLS od .NET Framework 4,6.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
ms.openlocfilehash: bb5aab3361663d7b5401d7e68688265fbc65b36f
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475356"
---
# <a name="mitigation-tls-protocols"></a><span data-ttu-id="3dd45-103">Omezení rizik: Protokoly TLS</span><span class="sxs-lookup"><span data-stu-id="3dd45-103">Mitigation: TLS Protocols</span></span>
<span data-ttu-id="3dd45-104">Počínaje .NET Framework 4,6 mohou <xref:System.Net.ServicePointManager?displayProperty=nameWithType> <xref:System.Net.Security.SslStream?displayProperty=nameWithType> třídy a používat jeden z následujících tří protokolů: TLS 1.0, TLS 1.1 nebo TLS 1,2.</span><span class="sxs-lookup"><span data-stu-id="3dd45-104">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager?displayProperty=nameWithType> and <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes are allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="3dd45-105">Protokol SSL 3.0 a šifra šifry nejsou podporované.</span><span class="sxs-lookup"><span data-stu-id="3dd45-105">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="3dd45-106">Dopad</span><span class="sxs-lookup"><span data-stu-id="3dd45-106">Impact</span></span>  
 <span data-ttu-id="3dd45-107">Tato změna má vliv na:</span><span class="sxs-lookup"><span data-stu-id="3dd45-107">This change affects:</span></span>  
  
- <span data-ttu-id="3dd45-108">Libovolná aplikace, která používá protokol SSL ke komunikaci se serverem HTTPS nebo serverem soketu pomocí některého z následujících typů: <xref:System.Net.Http.HttpClient> , <xref:System.Net.HttpWebRequest> , <xref:System.Net.FtpWebRequest> , <xref:System.Net.Mail.SmtpClient> a <xref:System.Net.Security.SslStream> .</span><span class="sxs-lookup"><span data-stu-id="3dd45-108">Any app that uses SSL to talk to an HTTPS server or a socket server using any of the following types: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, and <xref:System.Net.Security.SslStream>.</span></span>  
  
- <span data-ttu-id="3dd45-109">Všechny aplikace na straně serveru, které nelze upgradovat, aby podporovaly protokol TLS 1.0, TLS 1.1 nebo TLS 1,2..</span><span class="sxs-lookup"><span data-stu-id="3dd45-109">Any server-side app that cannot be upgraded to support Tls1.0, Tls1.1, or Tls 1.2..</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="3dd45-110">Omezení rizik</span><span class="sxs-lookup"><span data-stu-id="3dd45-110">Mitigation</span></span>  
 <span data-ttu-id="3dd45-111">Doporučené zmírnění je upgrade aplikace na straně serveru na TLS 1.0, TLS 1.1 nebo TLS 1,2.</span><span class="sxs-lookup"><span data-stu-id="3dd45-111">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="3dd45-112">Pokud to není možné, nebo pokud jsou klientské aplikace poškozeny, <xref:System.AppContext> můžete tuto funkci použít k odhlášení z těchto funkcí jedním ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="3dd45-112">If this is not feasible, or if client apps are broken, the <xref:System.AppContext> class can be used to opt out of this feature in either of two ways:</span></span>  
  
- <span data-ttu-id="3dd45-113">Prostřednictvím kódu programu, který je podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="3dd45-113">Programmatically, by using a code snippet like the following:</span></span>  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <span data-ttu-id="3dd45-114">Vzhledem k tomu, že se <xref:System.Net.ServicePointManager> objekt inicializuje pouze jednou, definování těchto nastavení kompatibility musí být první věc, kterou aplikace dělá.</span><span class="sxs-lookup"><span data-stu-id="3dd45-114">Because the <xref:System.Net.ServicePointManager> object is initialized only once, defining these compatibility settings must be the first thing the application does.</span></span>  
  
- <span data-ttu-id="3dd45-115">Přidáním následujícího řádku do [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) části souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="3dd45-115">By adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 <span data-ttu-id="3dd45-116">Upozorňujeme však, že nedoporučujeme výchozí chování, protože aplikace snižuje zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3dd45-116">Note, however, that opting out of the default behavior is not recommended, since it makes the application less secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3dd45-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="3dd45-117">See also</span></span>

- [<span data-ttu-id="3dd45-118">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="3dd45-118">Application compatibility</span></span>](application-compatibility.md)
