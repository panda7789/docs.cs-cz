---
title: HttpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
ms.openlocfilehash: 5e23342d57621554aaec67c5c568bb75202a9454
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59977038"
---
# <a name="httptransportbindingelement"></a><span data-ttu-id="350e6-102">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="350e6-102">HttpTransportBindingElement</span></span>
<span data-ttu-id="350e6-103">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="350e6-103">HttpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="350e6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="350e6-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="350e6-105">Metody</span><span class="sxs-lookup"><span data-stu-id="350e6-105">Methods</span></span>  
 <span data-ttu-id="350e6-106">Třída elementu HttpTransportBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="350e6-106">The HttpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="350e6-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="350e6-107">Properties</span></span>  
 <span data-ttu-id="350e6-108">Třída elementu HttpTransportBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="350e6-108">The HttpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="allowcookies"></a><span data-ttu-id="350e6-109">AllowCookies</span><span class="sxs-lookup"><span data-stu-id="350e6-109">AllowCookies</span></span>  
 <span data-ttu-id="350e6-110">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="350e6-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="350e6-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="350e6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="350e6-112">Hodnota, která určuje, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích.</span><span class="sxs-lookup"><span data-stu-id="350e6-112">A value that indicates whether the client accepts cookies and propagates them on future requests.</span></span>  
  
### <a name="authenticationscheme"></a><span data-ttu-id="350e6-113">AuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="350e6-113">AuthenticationScheme</span></span>  
 <span data-ttu-id="350e6-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="350e6-114">Data type: string</span></span>  
  
 <span data-ttu-id="350e6-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="350e6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="350e6-116">Schéma ověření použité pro ověřování požadavků klientů, jenž jsou zpracovány při naslouchání protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="350e6-116">The authentication scheme used to authenticate client requests being processed by an HTTP listener.</span></span>  
  
### <a name="bypassproxyonlocal"></a><span data-ttu-id="350e6-117">BypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="350e6-117">BypassProxyOnLocal</span></span>  
 <span data-ttu-id="350e6-118">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="350e6-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="350e6-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="350e6-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="350e6-120">Hodnota, která určuje, zda jsou proxy servery pro lokální adresy ignorovány.</span><span class="sxs-lookup"><span data-stu-id="350e6-120">A value that indicates whether proxies are ignored for local addresses.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="350e6-121">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="350e6-121">HostNameComparisonMode</span></span>  
 <span data-ttu-id="350e6-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="350e6-122">Data type: string</span></span>  
  
 <span data-ttu-id="350e6-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="350e6-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="350e6-124">Hodnota, která určuje, zda je ke zpřístupnění služby při shodě s identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="350e6-124">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="keepaliveenabled"></a><span data-ttu-id="350e6-125">KeepAliveEnabled</span><span class="sxs-lookup"><span data-stu-id="350e6-125">KeepAliveEnabled</span></span>  
 <span data-ttu-id="350e6-126">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="350e6-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="350e6-127">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="350e6-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="350e6-128">Při povolení připojení protokolu HTTP jsou zachováno bez ohledu na úroveň činnosti.</span><span class="sxs-lookup"><span data-stu-id="350e6-128">When enabled, HTTP connections are kept alive regardless of activity level.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="350e6-129">MaxBufferSize</span><span class="sxs-lookup"><span data-stu-id="350e6-129">MaxBufferSize</span></span>  
 <span data-ttu-id="350e6-130">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="350e6-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="350e6-131">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="350e6-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="350e6-132">Maximální velikost fondu vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="350e6-132">The maximum size of the buffer pool.</span></span>  
  
### <a name="proxyaddress"></a><span data-ttu-id="350e6-133">ProxyAddress</span><span class="sxs-lookup"><span data-stu-id="350e6-133">ProxyAddress</span></span>  
 <span data-ttu-id="350e6-134">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="350e6-134">Data type: string</span></span>  
  
 <span data-ttu-id="350e6-135">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="350e6-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="350e6-136">Identifikátor URI, který obsahuje adresu proxy serveru použitého pro požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="350e6-136">A URI that contains the address of the proxy to use for HTTP requests.</span></span>  
  
### <a name="proxyauthenticationscheme"></a><span data-ttu-id="350e6-137">ProxyAuthenticationScheme</span><span class="sxs-lookup"><span data-stu-id="350e6-137">ProxyAuthenticationScheme</span></span>  
 <span data-ttu-id="350e6-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="350e6-138">Data type: string</span></span>  
  
 <span data-ttu-id="350e6-139">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="350e6-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="350e6-140">Schéma ověření použité pro ověřování požadavků klientů zpracovávaných HTTP proxy.</span><span class="sxs-lookup"><span data-stu-id="350e6-140">The authentication scheme used to authenticate client requests being processed by an HTTP proxy.</span></span>  
  
### <a name="realm"></a><span data-ttu-id="350e6-141">Sféra</span><span class="sxs-lookup"><span data-stu-id="350e6-141">Realm</span></span>  
 <span data-ttu-id="350e6-142">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="350e6-142">Data type: string</span></span>  
  
 <span data-ttu-id="350e6-143">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="350e6-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="350e6-144">Sféra ověření.</span><span class="sxs-lookup"><span data-stu-id="350e6-144">The authentication realm.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="350e6-145">TransferMode</span><span class="sxs-lookup"><span data-stu-id="350e6-145">TransferMode</span></span>  
 <span data-ttu-id="350e6-146">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="350e6-146">Data type: string</span></span>  
  
 <span data-ttu-id="350e6-147">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="350e6-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="350e6-148">Hodnota, která určuje, zda jsou zprávy ukládány do vyrovnávací paměti nebo prostřednictvím datového proudu nebo žádost nebo odpověď.</span><span class="sxs-lookup"><span data-stu-id="350e6-148">A value that specifies whether messages are buffered or streamed or a request or response.</span></span>  
  
### <a name="unsafeconnectionntlmauthentication"></a><span data-ttu-id="350e6-149">UnsafeConnectionNtlmAuthentication</span><span class="sxs-lookup"><span data-stu-id="350e6-149">UnsafeConnectionNtlmAuthentication</span></span>  
 <span data-ttu-id="350e6-150">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="350e6-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="350e6-151">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="350e6-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="350e6-152">Hodnota, která určuje, zda je na serveru povoleno nezabezpečené sdílení připojení.</span><span class="sxs-lookup"><span data-stu-id="350e6-152">A value that indicates whether Unsafe Connection Sharing is enabled on the server.</span></span>  
  
### <a name="usedefaultwebproxy"></a><span data-ttu-id="350e6-153">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="350e6-153">UseDefaultWebProxy</span></span>  
 <span data-ttu-id="350e6-154">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="350e6-154">Data type: boolean</span></span>  
  
 <span data-ttu-id="350e6-155">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="350e6-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="350e6-156">Hodnota, která určuje, jestli uživatelovo specifické nastavení jsou upřednostňována nastavení proxy pro celý počítač.</span><span class="sxs-lookup"><span data-stu-id="350e6-156">A value that indicates whether the machine-wide proxy settings are used rather than the user specific settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="350e6-157">Požadavky</span><span class="sxs-lookup"><span data-stu-id="350e6-157">Requirements</span></span>  
  
|<span data-ttu-id="350e6-158">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="350e6-158">MOF</span></span>|<span data-ttu-id="350e6-159">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="350e6-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="350e6-160">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="350e6-160">Namespace</span></span>|<span data-ttu-id="350e6-161">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="350e6-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="350e6-162">Viz také:</span><span class="sxs-lookup"><span data-stu-id="350e6-162">See also</span></span>

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
