---
title: Zmírnění Protokoly TLS
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e98b447028ef9fa96233a71133aa82184d83cec8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779165"
---
# <a name="mitigation-tls-protocols"></a><span data-ttu-id="b636b-102">Zmírnění Protokoly TLS</span><span class="sxs-lookup"><span data-stu-id="b636b-102">Mitigation: TLS Protocols</span></span>
<span data-ttu-id="b636b-103">Počínaje .NET Framework 4,6 <xref:System.Net.ServicePointManager?displayProperty=nameWithType> mohou třídy a <xref:System.Net.Security.SslStream?displayProperty=nameWithType> používat jeden z následujících tří protokolů: TLS 1.0, TLS 1.1 nebo TLS 1,2.</span><span class="sxs-lookup"><span data-stu-id="b636b-103">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager?displayProperty=nameWithType> and <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes are allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="b636b-104">Protokol SSL 3.0 a šifra šifry nejsou podporované.</span><span class="sxs-lookup"><span data-stu-id="b636b-104">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="b636b-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="b636b-105">Impact</span></span>  
 <span data-ttu-id="b636b-106">Tato změna má vliv na:</span><span class="sxs-lookup"><span data-stu-id="b636b-106">This change affects:</span></span>  
  
- <span data-ttu-id="b636b-107">Libovolná aplikace, která používá protokol SSL ke komunikaci se serverem HTTPS nebo serverem soketu pomocí některého z následujících typů <xref:System.Net.Http.HttpClient>: <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, a <xref:System.Net.Security.SslStream>.</span><span class="sxs-lookup"><span data-stu-id="b636b-107">Any app that uses SSL to talk to an HTTPS server or a socket server using any of the following types: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, and <xref:System.Net.Security.SslStream>.</span></span>  
  
- <span data-ttu-id="b636b-108">Všechny aplikace na straně serveru, které nelze upgradovat, aby podporovaly protokol TLS 1.0, TLS 1.1 nebo TLS 1,2..</span><span class="sxs-lookup"><span data-stu-id="b636b-108">Any server-side app that cannot be upgraded to support Tls1.0, Tls1.1, or Tls 1.2..</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="b636b-109">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="b636b-109">Mitigation</span></span>  
 <span data-ttu-id="b636b-110">Doporučené zmírnění je upgrade aplikace na straně serveru na TLS 1.0, TLS 1.1 nebo TLS 1,2.</span><span class="sxs-lookup"><span data-stu-id="b636b-110">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="b636b-111">Pokud to není možné, nebo pokud jsou klientské aplikace poškozeny, <xref:System.AppContext> můžete tuto funkci použít k odhlášení z těchto funkcí jedním ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="b636b-111">If this is not feasible, or if client apps are broken, the <xref:System.AppContext> class can be used to opt out of this feature in either of two ways:</span></span>  
  
- <span data-ttu-id="b636b-112">Prostřednictvím kódu programu, který je podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="b636b-112">Programmatically, by using a code snippet like the following:</span></span>  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <span data-ttu-id="b636b-113">Vzhledem k tomu, že se objektinicializujepouzejednou,definovánítěchtonastaveníkompatibilitymusíbýtprvnívěc,kterouaplikacedělá.<xref:System.Net.ServicePointManager></span><span class="sxs-lookup"><span data-stu-id="b636b-113">Because the <xref:System.Net.ServicePointManager> object is initialized only once, defining these compatibility settings must be the first thing the application does.</span></span>  
  
- <span data-ttu-id="b636b-114">Přidáním následujícího řádku do [ \<části > modulu runtime](../configure-apps/file-schema/runtime/runtime-element.md) souboru App. config:</span><span class="sxs-lookup"><span data-stu-id="b636b-114">By adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 <span data-ttu-id="b636b-115">Upozorňujeme však, že nedoporučujeme výchozí chování, protože aplikace snižuje zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b636b-115">Note, however, that opting out of the default behavior is not recommended, since it makes the application less secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b636b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b636b-116">See also</span></span>

- [<span data-ttu-id="b636b-117">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="b636b-117">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6.md)
