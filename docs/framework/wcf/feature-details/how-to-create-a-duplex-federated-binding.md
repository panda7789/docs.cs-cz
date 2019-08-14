---
title: 'Postupy: Vytvoření duplexní federované vazby'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 71c970fa45d7d4ccd55fceddb2360d0aa0a768f8
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972062"
---
# <a name="how-to-create-a-duplex-federated-binding"></a><span data-ttu-id="4761c-102">Postupy: Vytvoření duplexní federované vazby</span><span class="sxs-lookup"><span data-stu-id="4761c-102">How to: Create a Duplex Federated Binding</span></span>

<span data-ttu-id="4761c-103"><xref:System.ServiceModel.WSFederationHttpBinding>podporuje pouze kontrakty pro výměnu zpráv datagram a Request/Reply.</span><span class="sxs-lookup"><span data-stu-id="4761c-103"><xref:System.ServiceModel.WSFederationHttpBinding> only supports the datagram and request/reply message exchange contracts.</span></span> <span data-ttu-id="4761c-104">Pokud chcete použít oboustrannou smlouvu výměny zpráv, musíte vytvořit vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="4761c-104">To use the duplex message exchange contract, you must create a custom binding.</span></span> <span data-ttu-id="4761c-105">Následující postupy ukazují, jak to provést v konfiguraci, použití zabezpečení režimu zprávy pro přenosy HTTP a TCP a použití smíšeného režimu zabezpečení pro přenos TCP.</span><span class="sxs-lookup"><span data-stu-id="4761c-105">The following procedures show how to do this in configuration, using Message mode security for the HTTP and TCP transports, and using mixed mode security for the TCP transport.</span></span> <span data-ttu-id="4761c-106">Vzorový kód zobrazující všechny 3 vazby jsou na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4761c-106">Sample code showing all 3 bindings is at the end of this topic.</span></span>

<span data-ttu-id="4761c-107">Vazbu můžete vytvořit také v kódu.</span><span class="sxs-lookup"><span data-stu-id="4761c-107">You can also create the binding in code.</span></span> <span data-ttu-id="4761c-108">Popis prvků vazby, které se mají vytvořit, najdete v tématu [How to: Vytvořte vlastní vazbu pomocí SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="4761c-108">For a description of the binding elements stack to create, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a><span data-ttu-id="4761c-109">Vytvoření duplexní federované vlastní vazby pomocí protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="4761c-109">To create a duplex federated custom binding with HTTP</span></span>

1. <span data-ttu-id="4761c-110">V uzlu [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) vazby > konfiguračního souboru vytvořte prvek > CustomBinding. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)</span><span class="sxs-lookup"><span data-stu-id="4761c-110">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="4761c-111">`name` `FederationDuplexHttpMessageSecurityBinding` [ Uvnitř\<prvkuCustomBinding > vytvořte vazbu >](../../../../docs/framework/misc/binding.md) elementu s atributem nastaveným na. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="4761c-111">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexHttpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="4761c-112">Uvnitř elementu > `authenticationMode` `SecureConversation`vazbyvytvořteprvek [zabezpečení > s atributem nastaveným na. \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ \<](../../../../docs/framework/misc/binding.md)</span><span class="sxs-lookup"><span data-stu-id="4761c-112">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="4761c-113">`IssuedTokenForCertificate` `authenticationMode` `IssuedTokenForSslNegotiated` [ Uvnitř\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ elementu>zabezpečenívytvořteprvek>secureConversationBootstrapsatributem\<](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) nastaveným na nebo.</span><span class="sxs-lookup"><span data-stu-id="4761c-113">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="4761c-114">Po elementu [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) [> zabezpečenívytvořteprázdný>elementcompositeDuplex.\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="4761c-114">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element.</span></span>

6. <span data-ttu-id="4761c-115">[ \<](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) [ PocompositeDuplex>elementuvytvořteprázdný>elementoneWay.\<](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md)</span><span class="sxs-lookup"><span data-stu-id="4761c-115">Following the [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element, create an empty [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element.</span></span>

7. <span data-ttu-id="4761c-116">Po elementu [> oneWayvytvořteprázdnýelement>HttpTransport.\<](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)</span><span class="sxs-lookup"><span data-stu-id="4761c-116">Following the [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element, create an empty [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a><span data-ttu-id="4761c-117">Vytvoření duplexní federované vlastní vazby pomocí režimu zabezpečení zprávy TCP</span><span class="sxs-lookup"><span data-stu-id="4761c-117">To create a duplex federated custom binding with TCP message security mode</span></span>

1. <span data-ttu-id="4761c-118">V uzlu [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) vazby > konfiguračního souboru vytvořte prvek > CustomBinding. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)</span><span class="sxs-lookup"><span data-stu-id="4761c-118">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="4761c-119">`name` `FederationDuplexTcpMessageSecurityBinding` [ Uvnitř\<prvkuCustomBinding > vytvořte vazbu >](../../../../docs/framework/misc/binding.md) elementu s atributem nastaveným na. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="4761c-119">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexTcpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="4761c-120">Uvnitř elementu > `authenticationMode` `SecureConversation`vazbyvytvořteprvek [zabezpečení > s atributem nastaveným na. \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ \<](../../../../docs/framework/misc/binding.md)</span><span class="sxs-lookup"><span data-stu-id="4761c-120">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="4761c-121">`IssuedTokenForCertificate` `authenticationMode` `IssuedTokenForSslNegotiated` [ Uvnitř\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ elementu>zabezpečenívytvořteprvek>secureConversationBootstrapsatributem\<](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) nastaveným na nebo.</span><span class="sxs-lookup"><span data-stu-id="4761c-121">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="4761c-122">Po elementu [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) [> zabezpečenívytvořteprázdný>elementtcpTransport.\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="4761c-122">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a><span data-ttu-id="4761c-123">Vytvoření duplexní federované vlastní vazby se smíšeným režimem zabezpečení TCP</span><span class="sxs-lookup"><span data-stu-id="4761c-123">To create a duplex federated custom binding with TCP mixed security mode</span></span>

1. <span data-ttu-id="4761c-124">V uzlu [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) vazby > konfiguračního souboru vytvořte prvek > CustomBinding. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)</span><span class="sxs-lookup"><span data-stu-id="4761c-124">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="4761c-125">`name` `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding` [ Uvnitř\<prvkuCustomBinding > vytvořte vazbu >](../../../../docs/framework/misc/binding.md) elementu s atributem nastaveným na. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="4761c-125">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span></span>

3. <span data-ttu-id="4761c-126">Uvnitř elementu > `authenticationMode` `SecureConversation`vazbyvytvořteprvek [zabezpečení > s atributem nastaveným na. \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ \<](../../../../docs/framework/misc/binding.md)</span><span class="sxs-lookup"><span data-stu-id="4761c-126">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="4761c-127">`IssuedTokenForCertificate` `authenticationMode` `IssuedTokenForSslNegotiated` [ Uvnitř\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) [ elementu>zabezpečenívytvořteprvek>secureConversationBootstrapsatributem\<](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) nastaveným na nebo.</span><span class="sxs-lookup"><span data-stu-id="4761c-127">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="4761c-128">Po elementu [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) [> zabezpečenívytvořteprázdný>elementsslStreamSecurity.\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="4761c-128">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span></span>

6. <span data-ttu-id="4761c-129">Po elementu [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) sslStreamSecurity > Vytvořte prázdný tcpTransport prvek >. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md)</span><span class="sxs-lookup"><span data-stu-id="4761c-129">Following the [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="code-sample"></a><span data-ttu-id="4761c-130">Ukázka kódu</span><span class="sxs-lookup"><span data-stu-id="4761c-130">Code Sample</span></span>

### <a name="sample-with-3-bindings"></a><span data-ttu-id="4761c-131">Ukázka se 3 vazbami</span><span class="sxs-lookup"><span data-stu-id="4761c-131">Sample with 3 Bindings</span></span>

1. <span data-ttu-id="4761c-132">Do konfiguračního souboru vložte následující kód.</span><span class="sxs-lookup"><span data-stu-id="4761c-132">Insert the following code into your configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="4761c-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="4761c-133">Example</span></span>

```xml
<bindings>
   <customBinding>
      <binding name="FederationDuplexHttpMessageSecurityBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />
          </security>
          <compositeDuplex />
          <oneWay />
          <httpTransport />
       </binding>
<!-- duplex over https is not supported -->
       <binding name="FederationDuplexTcpMessageSecurityBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />
          </security>
          <tcpTransport />
       </binding>
       <binding name="FederationDuplexTcpTransportSecurityWithMessageCredentialsBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenOverTransport" />
          </security>
<!-- requireClientCertificate = true or <windowsStreamSecurity /> can be used, but does not make sense for most scenarios -->
          <sslStreamSecurity />
          <tcpTransport />
       </binding>
    </customBinding>
</bindings>
```
