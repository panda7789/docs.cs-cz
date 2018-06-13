---
title: 'Omezení rizik: Protokoly TLS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 33f97d13-3022-43da-8b18-cdb5c88df9c2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d5d37326d0278225146d217624508e7c7738375b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33388258"
---
# <a name="mitigation-tls-protocols"></a><span data-ttu-id="316a8-102">Omezení rizik: Protokoly TLS</span><span class="sxs-lookup"><span data-stu-id="316a8-102">Mitigation: TLS Protocols</span></span>
<span data-ttu-id="316a8-103">Od verze rozhraní .NET Framework 4.6 <xref:System.Net.ServicePointManager?displayProperty=nameWithType> a <xref:System.Net.Security.SslStream?displayProperty=nameWithType> třídy mohou používat jednu z následujících tří protokolů: Tls1.0, Tls1.1 nebo Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="316a8-103">Starting with the .NET Framework 4.6, the <xref:System.Net.ServicePointManager?displayProperty=nameWithType> and <xref:System.Net.Security.SslStream?displayProperty=nameWithType> classes are allowed to use one of the following three protocols: Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="316a8-104">Protokol SSL3.0 a šifrovací algoritmus RC4 nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="316a8-104">The SSL3.0 protocol and RC4 cipher are not supported.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="316a8-105">Dopad</span><span class="sxs-lookup"><span data-stu-id="316a8-105">Impact</span></span>  
 <span data-ttu-id="316a8-106">Tato změna ovlivňuje:</span><span class="sxs-lookup"><span data-stu-id="316a8-106">This change affects:</span></span>  
  
-   <span data-ttu-id="316a8-107">Jakékoli aplikaci, která používá protokol SSL, aby komunikoval s serveru HTTPS nebo server soketu pomocí kteréhokoli z následujících typů: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, a <xref:System.Net.Security.SslStream>.</span><span class="sxs-lookup"><span data-stu-id="316a8-107">Any app that uses SSL to talk to an HTTPS server or a socket server using any of the following types: <xref:System.Net.Http.HttpClient>, <xref:System.Net.HttpWebRequest>, <xref:System.Net.FtpWebRequest>, <xref:System.Net.Mail.SmtpClient>, and <xref:System.Net.Security.SslStream>.</span></span>  
  
-   <span data-ttu-id="316a8-108">Jakékoli serverovou aplikaci, která nejde upgradovat na podporu Tls1.0, Tls1.1 nebo Tls 1.2...</span><span class="sxs-lookup"><span data-stu-id="316a8-108">Any server-side app that cannot be upgraded to support Tls1.0, Tls1.1, or Tls 1.2..</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="316a8-109">Zmírnění</span><span class="sxs-lookup"><span data-stu-id="316a8-109">Mitigation</span></span>  
 <span data-ttu-id="316a8-110">Doporučené omezení rizik se k upgradu aplikace na straně serveru Tls1.0, Tls1.1 nebo Tls 1.2.</span><span class="sxs-lookup"><span data-stu-id="316a8-110">The recommended mitigation is to upgrade the sever-side app to Tls1.0, Tls1.1, or Tls 1.2.</span></span> <span data-ttu-id="316a8-111">Pokud to není možné, nebo pokud klientských aplikací jsou poškozená, <xref:System.AppContext> třídu lze použít pro vyjádření výslovného nesouhlasu tuto funkci v některém ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="316a8-111">If this is not feasible, or if client apps are broken, the <xref:System.AppContext> class can be used to opt out of this feature in either of two ways:</span></span>  
  
-   <span data-ttu-id="316a8-112">Programově pomocí fragmentu kódu takto:</span><span class="sxs-lookup"><span data-stu-id="316a8-112">Programmatically, by using a code snippet like the following:</span></span>  
  
     [!code-csharp[AppCompat.SSLProtocols#1](../../../samples/snippets/csharp/VS_Snippets_CLR/appcompat.sslprotocols/cs/program.cs#1)]
     [!code-vb[AppCompat.SSLProtocols#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/appcompat.sslprotocols/vb/module1.vb#1)]  
  
     <span data-ttu-id="316a8-113">Protože <xref:System.Net.ServicePointManager> objekt je inicializovat pouze jednou, definování těchto nastavení kompatibility musí být první věc, kterou aplikace.</span><span class="sxs-lookup"><span data-stu-id="316a8-113">Because the <xref:System.Net.ServicePointManager> object is initialized only once, defining these compatibility settings must be the first thing the application does.</span></span>  
  
-   <span data-ttu-id="316a8-114">Přidáním následující řádek [ \<runtime >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) části souboru app.config:</span><span class="sxs-lookup"><span data-stu-id="316a8-114">By adding the following line to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
    ```xml  
    <AppContextSwitchOverrides value="Switch.System.Net.DontEnableSchUseStrongCrypto=true"/>  
    ```  
  
 <span data-ttu-id="316a8-115">Upozorňujeme však, že zrušení výchozí chování se nedoporučuje, protože způsobí, že aplikace méně bezpečné.</span><span class="sxs-lookup"><span data-stu-id="316a8-115">Note, however, that opting out of the default behavior is not recommended, since it makes the application less secure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="316a8-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="316a8-116">See Also</span></span>  
 [<span data-ttu-id="316a8-117">Odlišnosti ve změnách cílení</span><span class="sxs-lookup"><span data-stu-id="316a8-117">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
