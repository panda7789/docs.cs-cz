---
title: HttpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
ms.openlocfilehash: 1975fd2e04a5c9cdb68bc838802abafbd781b7e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487017"
---
# <a name="httptransportbindingelement"></a><span data-ttu-id="254f2-102">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="254f2-102">HttpTransportBindingElement</span></span>
<span data-ttu-id="254f2-103">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="254f2-103">HttpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="254f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="254f2-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="254f2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="254f2-105">Methods</span></span>  
 <span data-ttu-id="254f2-106">Třída HttpTransportBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="254f2-106">The HttpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="254f2-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="254f2-107">Properties</span></span>  
 <span data-ttu-id="254f2-108">Třída HttpTransportBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="254f2-108">The HttpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="allowcookies"></a><span data-ttu-id="254f2-109">allowCookies</span><span class="sxs-lookup"><span data-stu-id="254f2-109">AllowCookies</span></span>  
 <span data-ttu-id="254f2-110">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="254f2-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="254f2-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="254f2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="254f2-112">Hodnota, která určuje, jestli klient přijímá soubory cookie a rozšiřuje je na dalších požadavků.</span><span class="sxs-lookup"><span data-stu-id="254f2-112">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span>  
  
### <a name="authenticationscheme"></a><span data-ttu-id="254f2-113">AuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="254f2-113">AuthenticationScheme</span></span>  
 <span data-ttu-id="254f2-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="254f2-114">Data type: string</span></span>  
  
 <span data-ttu-id="254f2-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="254f2-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="254f2-116">Schéma ověřování používá k ověření klientských požadavků zpracovávaných naslouchací proces protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="254f2-116">The authentication scheme used to authenticate client requests being processed by an HTTP listener.</span></span>  
  
### <a name="bypassproxyonlocal"></a><span data-ttu-id="254f2-117">BypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="254f2-117">BypassProxyOnLocal</span></span>  
 <span data-ttu-id="254f2-118">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="254f2-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="254f2-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="254f2-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="254f2-120">Hodnota, která označuje, zda jsou ignorovány proxy pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="254f2-120">A value that indicates whether proxies are ignored for local addresses.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="254f2-121">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="254f2-121">HostNameComparisonMode</span></span>  
 <span data-ttu-id="254f2-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="254f2-122">Data type: string</span></span>  
  
 <span data-ttu-id="254f2-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="254f2-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="254f2-124">Hodnota, která označuje, zda se ke zpřístupnění služby při shodujícím v identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="254f2-124">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="keepaliveenabled"></a><span data-ttu-id="254f2-125">KeepAliveEnabled</span><span class="sxs-lookup"><span data-stu-id="254f2-125">KeepAliveEnabled</span></span>  
 <span data-ttu-id="254f2-126">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="254f2-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="254f2-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="254f2-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="254f2-128">Když je povolené, udržely připojení prostřednictvím protokolu HTTP aktivní bez ohledu na úrovni aktivity.</span><span class="sxs-lookup"><span data-stu-id="254f2-128">When enabled, HTTP connections are kept alive regardless of activity level.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="254f2-129">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="254f2-129">MaxBufferSize</span></span>  
 <span data-ttu-id="254f2-130">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="254f2-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="254f2-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="254f2-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="254f2-132">Maximální velikost fondu vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="254f2-132">The maximum size of the buffer pool.</span></span>  
  
### <a name="proxyaddress"></a><span data-ttu-id="254f2-133">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="254f2-133">ProxyAddress</span></span>  
 <span data-ttu-id="254f2-134">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="254f2-134">Data type: string</span></span>  
  
 <span data-ttu-id="254f2-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="254f2-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="254f2-136">Identifikátor URI, který obsahuje adresu proxy, který chcete použít pro požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="254f2-136">A URI that contains the address of the proxy to use for HTTP requests.</span></span>  
  
### <a name="proxyauthenticationscheme"></a><span data-ttu-id="254f2-137">ProxyAuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="254f2-137">ProxyAuthenticationScheme</span></span>  
 <span data-ttu-id="254f2-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="254f2-138">Data type: string</span></span>  
  
 <span data-ttu-id="254f2-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="254f2-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="254f2-140">Schéma ověřování používá k ověření klientských požadavků zpracovávaných proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="254f2-140">The authentication scheme used to authenticate client requests being processed by an HTTP proxy.</span></span>  
  
### <a name="realm"></a><span data-ttu-id="254f2-141">sféry</span><span class="sxs-lookup"><span data-stu-id="254f2-141">Realm</span></span>  
 <span data-ttu-id="254f2-142">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="254f2-142">Data type: string</span></span>  
  
 <span data-ttu-id="254f2-143">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="254f2-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="254f2-144">Sféra ověření.</span><span class="sxs-lookup"><span data-stu-id="254f2-144">The authentication realm.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="254f2-145">transferMode</span><span class="sxs-lookup"><span data-stu-id="254f2-145">TransferMode</span></span>  
 <span data-ttu-id="254f2-146">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="254f2-146">Data type: string</span></span>  
  
 <span data-ttu-id="254f2-147">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="254f2-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="254f2-148">Hodnotu, která určuje, zda jsou zprávy do vyrovnávací paměti nebo prostřednictvím datového proudu nebo požadavku nebo odpovědi.</span><span class="sxs-lookup"><span data-stu-id="254f2-148">A value that specifies whether messages are buffered or streamed or a request or response.</span></span>  
  
### <a name="unsafeconnectionntlmauthentication"></a><span data-ttu-id="254f2-149">UnsafeConnectionNtlmAuthentication</span><span class="sxs-lookup"><span data-stu-id="254f2-149">UnsafeConnectionNtlmAuthentication</span></span>  
 <span data-ttu-id="254f2-150">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="254f2-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="254f2-151">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="254f2-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="254f2-152">Hodnota, která určuje, zda je na serveru povoleno sdílení nezabezpečené připojení.</span><span class="sxs-lookup"><span data-stu-id="254f2-152">A value that indicates whether Unsafe Connection Sharing is enabled on the server.</span></span>  
  
### <a name="usedefaultwebproxy"></a><span data-ttu-id="254f2-153">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="254f2-153">UseDefaultWebProxy</span></span>  
 <span data-ttu-id="254f2-154">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="254f2-154">Data type: boolean</span></span>  
  
 <span data-ttu-id="254f2-155">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="254f2-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="254f2-156">Hodnota, která určuje, zda jsou nastavení proxy serveru celého systému použít místo nastavení specifická pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="254f2-156">A value that indicates whether the machine-wide proxy settings are used rather than the user specific settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="254f2-157">Požadavky</span><span class="sxs-lookup"><span data-stu-id="254f2-157">Requirements</span></span>  
  
|<span data-ttu-id="254f2-158">MOF</span><span class="sxs-lookup"><span data-stu-id="254f2-158">MOF</span></span>|<span data-ttu-id="254f2-159">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="254f2-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="254f2-160">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="254f2-160">Namespace</span></span>|<span data-ttu-id="254f2-161">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="254f2-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="254f2-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="254f2-162">See Also</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
