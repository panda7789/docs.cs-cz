---
title: HttpTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 612f2eb04ae3449fddc8fb871683b26138d046d2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="httptransportbindingelement"></a><span data-ttu-id="29ff7-102">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="29ff7-102">HttpTransportBindingElement</span></span>
<span data-ttu-id="29ff7-103">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="29ff7-103">HttpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29ff7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29ff7-104">Syntax</span></span>  
  
```  
class HttpTransportBindingElement : TransportBindingElement  
{  
  boolean AllowCookies;  
  string AuthenticationScheme;  
  boolean BypassProxyOnLocal;  
  string HostNameComparisonMode;  
  boolean KeepAliveEnabled;  
  sint32 MaxBufferSize;  
  string ProxyAddress;  
  string ProxyAuthenticationScheme;  
  string Realm;  
  string TransferMode;  
  boolean UnsafeConnectionNtlmAuthentication;  
  boolean UseDefaultWebProxy;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="29ff7-105">Metody</span><span class="sxs-lookup"><span data-stu-id="29ff7-105">Methods</span></span>  
 <span data-ttu-id="29ff7-106">Třída HttpTransportBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="29ff7-106">The HttpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="29ff7-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="29ff7-107">Properties</span></span>  
 <span data-ttu-id="29ff7-108">Třída HttpTransportBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="29ff7-108">The HttpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="allowcookies"></a><span data-ttu-id="29ff7-109">allowCookies</span><span class="sxs-lookup"><span data-stu-id="29ff7-109">AllowCookies</span></span>  
 <span data-ttu-id="29ff7-110">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="29ff7-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="29ff7-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="29ff7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="29ff7-112">Hodnota, která určuje, jestli klient přijímá soubory cookie a rozšiřuje je na dalších požadavků.</span><span class="sxs-lookup"><span data-stu-id="29ff7-112">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span>  
  
### <a name="authenticationscheme"></a><span data-ttu-id="29ff7-113">AuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="29ff7-113">AuthenticationScheme</span></span>  
 <span data-ttu-id="29ff7-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="29ff7-114">Data type: string</span></span>  
  
 <span data-ttu-id="29ff7-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="29ff7-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="29ff7-116">Schéma ověřování používá k ověření klientských požadavků zpracovávaných naslouchací proces protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="29ff7-116">The authentication scheme used to authenticate client requests being processed by an HTTP listener.</span></span>  
  
### <a name="bypassproxyonlocal"></a><span data-ttu-id="29ff7-117">BypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="29ff7-117">BypassProxyOnLocal</span></span>  
 <span data-ttu-id="29ff7-118">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="29ff7-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="29ff7-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="29ff7-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="29ff7-120">Hodnota, která označuje, zda jsou ignorovány proxy pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="29ff7-120">A value that indicates whether proxies are ignored for local addresses.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="29ff7-121">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="29ff7-121">HostNameComparisonMode</span></span>  
 <span data-ttu-id="29ff7-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="29ff7-122">Data type: string</span></span>  
  
 <span data-ttu-id="29ff7-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="29ff7-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="29ff7-124">Hodnota, která označuje, zda se ke zpřístupnění služby při shodujícím v identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="29ff7-124">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="keepaliveenabled"></a><span data-ttu-id="29ff7-125">KeepAliveEnabled</span><span class="sxs-lookup"><span data-stu-id="29ff7-125">KeepAliveEnabled</span></span>  
 <span data-ttu-id="29ff7-126">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="29ff7-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="29ff7-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="29ff7-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="29ff7-128">Když je povolené, udržely připojení prostřednictvím protokolu HTTP aktivní bez ohledu na úrovni aktivity.</span><span class="sxs-lookup"><span data-stu-id="29ff7-128">When enabled, HTTP connections are kept alive regardless of activity level.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="29ff7-129">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="29ff7-129">MaxBufferSize</span></span>  
 <span data-ttu-id="29ff7-130">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="29ff7-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="29ff7-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="29ff7-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="29ff7-132">Maximální velikost fondu vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="29ff7-132">The maximum size of the buffer pool.</span></span>  
  
### <a name="proxyaddress"></a><span data-ttu-id="29ff7-133">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="29ff7-133">ProxyAddress</span></span>  
 <span data-ttu-id="29ff7-134">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="29ff7-134">Data type: string</span></span>  
  
 <span data-ttu-id="29ff7-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="29ff7-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="29ff7-136">Identifikátor URI, který obsahuje adresu proxy, který chcete použít pro požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="29ff7-136">A URI that contains the address of the proxy to use for HTTP requests.</span></span>  
  
### <a name="proxyauthenticationscheme"></a><span data-ttu-id="29ff7-137">ProxyAuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="29ff7-137">ProxyAuthenticationScheme</span></span>  
 <span data-ttu-id="29ff7-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="29ff7-138">Data type: string</span></span>  
  
 <span data-ttu-id="29ff7-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="29ff7-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="29ff7-140">Schéma ověřování používá k ověření klientských požadavků zpracovávaných proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="29ff7-140">The authentication scheme used to authenticate client requests being processed by an HTTP proxy.</span></span>  
  
### <a name="realm"></a><span data-ttu-id="29ff7-141">sféry</span><span class="sxs-lookup"><span data-stu-id="29ff7-141">Realm</span></span>  
 <span data-ttu-id="29ff7-142">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="29ff7-142">Data type: string</span></span>  
  
 <span data-ttu-id="29ff7-143">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="29ff7-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="29ff7-144">Sféra ověření.</span><span class="sxs-lookup"><span data-stu-id="29ff7-144">The authentication realm.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="29ff7-145">transferMode</span><span class="sxs-lookup"><span data-stu-id="29ff7-145">TransferMode</span></span>  
 <span data-ttu-id="29ff7-146">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="29ff7-146">Data type: string</span></span>  
  
 <span data-ttu-id="29ff7-147">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="29ff7-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="29ff7-148">Hodnotu, která určuje, zda jsou zprávy do vyrovnávací paměti nebo prostřednictvím datového proudu nebo požadavku nebo odpovědi.</span><span class="sxs-lookup"><span data-stu-id="29ff7-148">A value that specifies whether messages are buffered or streamed or a request or response.</span></span>  
  
### <a name="unsafeconnectionntlmauthentication"></a><span data-ttu-id="29ff7-149">UnsafeConnectionNtlmAuthentication</span><span class="sxs-lookup"><span data-stu-id="29ff7-149">UnsafeConnectionNtlmAuthentication</span></span>  
 <span data-ttu-id="29ff7-150">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="29ff7-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="29ff7-151">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="29ff7-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="29ff7-152">Hodnota, která určuje, zda je na serveru povoleno sdílení nezabezpečené připojení.</span><span class="sxs-lookup"><span data-stu-id="29ff7-152">A value that indicates whether Unsafe Connection Sharing is enabled on the server.</span></span>  
  
### <a name="usedefaultwebproxy"></a><span data-ttu-id="29ff7-153">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="29ff7-153">UseDefaultWebProxy</span></span>  
 <span data-ttu-id="29ff7-154">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="29ff7-154">Data type: boolean</span></span>  
  
 <span data-ttu-id="29ff7-155">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="29ff7-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="29ff7-156">Hodnota, která určuje, zda jsou nastavení proxy serveru celého systému použít místo nastavení specifická pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="29ff7-156">A value that indicates whether the machine-wide proxy settings are used rather than the user specific settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29ff7-157">Požadavky</span><span class="sxs-lookup"><span data-stu-id="29ff7-157">Requirements</span></span>  
  
|<span data-ttu-id="29ff7-158">MOF</span><span class="sxs-lookup"><span data-stu-id="29ff7-158">MOF</span></span>|<span data-ttu-id="29ff7-159">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="29ff7-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="29ff7-160">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="29ff7-160">Namespace</span></span>|<span data-ttu-id="29ff7-161">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="29ff7-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="29ff7-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="29ff7-162">See Also</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
