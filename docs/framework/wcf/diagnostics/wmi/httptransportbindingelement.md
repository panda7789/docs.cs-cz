---
title: HttpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
ms.openlocfilehash: 2376a0ec25539b97a37b1827e3e4c148eb8d5838
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610770"
---
# <a name="httptransportbindingelement"></a><span data-ttu-id="afba0-102">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="afba0-102">HttpTransportBindingElement</span></span>
<span data-ttu-id="afba0-103">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="afba0-103">HttpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afba0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afba0-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="afba0-105">Metody</span><span class="sxs-lookup"><span data-stu-id="afba0-105">Methods</span></span>  
 <span data-ttu-id="afba0-106">Třída elementu HttpTransportBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="afba0-106">The HttpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="afba0-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="afba0-107">Properties</span></span>  
 <span data-ttu-id="afba0-108">Třída elementu HttpTransportBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="afba0-108">The HttpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="allowcookies"></a><span data-ttu-id="afba0-109">AllowCookies</span><span class="sxs-lookup"><span data-stu-id="afba0-109">AllowCookies</span></span>  
 <span data-ttu-id="afba0-110">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="afba0-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="afba0-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="afba0-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="afba0-112">Hodnota, která určuje, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích.</span><span class="sxs-lookup"><span data-stu-id="afba0-112">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span>  
  
### <a name="authenticationscheme"></a><span data-ttu-id="afba0-113">AuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="afba0-113">AuthenticationScheme</span></span>  
 <span data-ttu-id="afba0-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="afba0-114">Data type: string</span></span>  
  
 <span data-ttu-id="afba0-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="afba0-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="afba0-116">Schéma ověření použité pro ověřování požadavků klientů, jenž jsou zpracovány při naslouchání protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="afba0-116">The authentication scheme used to authenticate client requests being processed by an HTTP listener.</span></span>  
  
### <a name="bypassproxyonlocal"></a><span data-ttu-id="afba0-117">BypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="afba0-117">BypassProxyOnLocal</span></span>  
 <span data-ttu-id="afba0-118">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="afba0-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="afba0-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="afba0-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="afba0-120">Hodnota, která určuje, zda jsou proxy servery pro lokální adresy ignorovány.</span><span class="sxs-lookup"><span data-stu-id="afba0-120">A value that indicates whether proxies are ignored for local addresses.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="afba0-121">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="afba0-121">HostNameComparisonMode</span></span>  
 <span data-ttu-id="afba0-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="afba0-122">Data type: string</span></span>  
  
 <span data-ttu-id="afba0-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="afba0-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="afba0-124">Hodnota, která určuje, zda je ke zpřístupnění služby při shodě s identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="afba0-124">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="keepaliveenabled"></a><span data-ttu-id="afba0-125">KeepAliveEnabled</span><span class="sxs-lookup"><span data-stu-id="afba0-125">KeepAliveEnabled</span></span>  
 <span data-ttu-id="afba0-126">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="afba0-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="afba0-127">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="afba0-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="afba0-128">Při povolení připojení protokolu HTTP jsou zachováno bez ohledu na úroveň činnosti.</span><span class="sxs-lookup"><span data-stu-id="afba0-128">When enabled, HTTP connections are kept alive regardless of activity level.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="afba0-129">MaxBufferSize</span><span class="sxs-lookup"><span data-stu-id="afba0-129">MaxBufferSize</span></span>  
 <span data-ttu-id="afba0-130">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="afba0-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="afba0-131">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="afba0-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="afba0-132">Maximální velikost fondu vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="afba0-132">The maximum size of the buffer pool.</span></span>  
  
### <a name="proxyaddress"></a><span data-ttu-id="afba0-133">ProxyAddress</span><span class="sxs-lookup"><span data-stu-id="afba0-133">ProxyAddress</span></span>  
 <span data-ttu-id="afba0-134">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="afba0-134">Data type: string</span></span>  
  
 <span data-ttu-id="afba0-135">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="afba0-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="afba0-136">Identifikátor URI, který obsahuje adresu proxy serveru použitého pro požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="afba0-136">A URI that contains the address of the proxy to use for HTTP requests.</span></span>  
  
### <a name="proxyauthenticationscheme"></a><span data-ttu-id="afba0-137">ProxyAuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="afba0-137">ProxyAuthenticationScheme</span></span>  
 <span data-ttu-id="afba0-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="afba0-138">Data type: string</span></span>  
  
 <span data-ttu-id="afba0-139">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="afba0-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="afba0-140">Schéma ověření použité pro ověřování požadavků klientů zpracovávaných HTTP proxy.</span><span class="sxs-lookup"><span data-stu-id="afba0-140">The authentication scheme used to authenticate client requests being processed by an HTTP proxy.</span></span>  
  
### <a name="realm"></a><span data-ttu-id="afba0-141">Sféra</span><span class="sxs-lookup"><span data-stu-id="afba0-141">Realm</span></span>  
 <span data-ttu-id="afba0-142">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="afba0-142">Data type: string</span></span>  
  
 <span data-ttu-id="afba0-143">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="afba0-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="afba0-144">Sféra ověření.</span><span class="sxs-lookup"><span data-stu-id="afba0-144">The authentication realm.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="afba0-145">TransferMode</span><span class="sxs-lookup"><span data-stu-id="afba0-145">TransferMode</span></span>  
 <span data-ttu-id="afba0-146">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="afba0-146">Data type: string</span></span>  
  
 <span data-ttu-id="afba0-147">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="afba0-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="afba0-148">Hodnota, která určuje, zda jsou zprávy ukládány do vyrovnávací paměti nebo prostřednictvím datového proudu nebo žádost nebo odpověď.</span><span class="sxs-lookup"><span data-stu-id="afba0-148">A value that specifies whether messages are buffered or streamed or a request or response.</span></span>  
  
### <a name="unsafeconnectionntlmauthentication"></a><span data-ttu-id="afba0-149">UnsafeConnectionNtlmAuthentication</span><span class="sxs-lookup"><span data-stu-id="afba0-149">UnsafeConnectionNtlmAuthentication</span></span>  
 <span data-ttu-id="afba0-150">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="afba0-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="afba0-151">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="afba0-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="afba0-152">Hodnota, která určuje, zda je na serveru povoleno nezabezpečené sdílení připojení.</span><span class="sxs-lookup"><span data-stu-id="afba0-152">A value that indicates whether Unsafe Connection Sharing is enabled on the server.</span></span>  
  
### <a name="usedefaultwebproxy"></a><span data-ttu-id="afba0-153">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="afba0-153">UseDefaultWebProxy</span></span>  
 <span data-ttu-id="afba0-154">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="afba0-154">Data type: boolean</span></span>  
  
 <span data-ttu-id="afba0-155">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="afba0-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="afba0-156">Hodnota, která určuje, jestli uživatelovo specifické nastavení jsou upřednostňována nastavení proxy pro celý počítač.</span><span class="sxs-lookup"><span data-stu-id="afba0-156">A value that indicates whether the machine-wide proxy settings are used rather than the user specific settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afba0-157">Požadavky</span><span class="sxs-lookup"><span data-stu-id="afba0-157">Requirements</span></span>  
  
|<span data-ttu-id="afba0-158">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="afba0-158">MOF</span></span>|<span data-ttu-id="afba0-159">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="afba0-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="afba0-160">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="afba0-160">Namespace</span></span>|<span data-ttu-id="afba0-161">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="afba0-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="afba0-162">Viz také:</span><span class="sxs-lookup"><span data-stu-id="afba0-162">See also</span></span>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
