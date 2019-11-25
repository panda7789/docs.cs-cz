---
title: 'Postupy: Vytvoření duplexní federované vazby'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 3ecd9e2dbeb30bb255cbf66488b50a9b20219431
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141716"
---
# <a name="how-to-create-a-duplex-federated-binding"></a><span data-ttu-id="ff341-102">Postupy: Vytvoření duplexní federované vazby</span><span class="sxs-lookup"><span data-stu-id="ff341-102">How to: Create a Duplex Federated Binding</span></span>

<span data-ttu-id="ff341-103"><xref:System.ServiceModel.WSFederationHttpBinding> podporuje jenom kontrakty datagramu a žádosti nebo odpovědi na zprávy o výměně.</span><span class="sxs-lookup"><span data-stu-id="ff341-103"><xref:System.ServiceModel.WSFederationHttpBinding> only supports the datagram and request/reply message exchange contracts.</span></span> <span data-ttu-id="ff341-104">Pokud chcete použít oboustrannou smlouvu výměny zpráv, musíte vytvořit vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="ff341-104">To use the duplex message exchange contract, you must create a custom binding.</span></span> <span data-ttu-id="ff341-105">Následující postupy ukazují, jak to provést v konfiguraci, použití zabezpečení režimu zprávy pro přenosy HTTP a TCP a použití smíšeného režimu zabezpečení pro přenos TCP.</span><span class="sxs-lookup"><span data-stu-id="ff341-105">The following procedures show how to do this in configuration, using Message mode security for the HTTP and TCP transports, and using mixed mode security for the TCP transport.</span></span> <span data-ttu-id="ff341-106">Vzorový kód zobrazující všechny 3 vazby jsou na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="ff341-106">Sample code showing all 3 bindings is at the end of this topic.</span></span>

<span data-ttu-id="ff341-107">Vazbu můžete vytvořit také v kódu.</span><span class="sxs-lookup"><span data-stu-id="ff341-107">You can also create the binding in code.</span></span> <span data-ttu-id="ff341-108">Popis prvků vazby, které se mají vytvořit, naleznete v tématu [How to: Create a Custom Binding using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="ff341-108">For a description of the binding elements stack to create, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a><span data-ttu-id="ff341-109">Vytvoření duplexní federované vlastní vazby pomocí protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="ff341-109">To create a duplex federated custom binding with HTTP</span></span>

1. <span data-ttu-id="ff341-110">V uzlu [\<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) konfiguračního souboru vytvořte prvek [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="ff341-110">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="ff341-111">Uvnitř [\<elementu > CustomBinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) vytvořte [\<vazba >](../../configure-apps/file-schema/wcf/bindings.md) element s atributem `name` nastaveným na `FederationDuplexHttpMessageSecurityBinding`.</span><span class="sxs-lookup"><span data-stu-id="ff341-111">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexHttpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="ff341-112">Uvnitř [\<vazba >](../../configure-apps/file-schema/wcf/bindings.md) elementu vytvořte [\<element zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) s atributem `authenticationMode` nastaveným na `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="ff341-112">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="ff341-113">Uvnitř prvku [\<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) vytvořte prvek [\<secureConversationBootstrap](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) s atributem `authenticationMode` nastaveným na `IssuedTokenForCertificate` nebo `IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="ff341-113">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="ff341-114">Po elementu [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) vytvořte prázdný prvek [\<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) .</span><span class="sxs-lookup"><span data-stu-id="ff341-114">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element.</span></span>

6. <span data-ttu-id="ff341-115">Po [\<elementu > compositeDuplex](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) vytvořte prázdný prvek [\<oneWay](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) .</span><span class="sxs-lookup"><span data-stu-id="ff341-115">Following the [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element, create an empty [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element.</span></span>

7. <span data-ttu-id="ff341-116">Po [\<prvku > oneWay](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) vytvořte prázdný [\<](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) element.</span><span class="sxs-lookup"><span data-stu-id="ff341-116">Following the [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element, create an empty [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a><span data-ttu-id="ff341-117">Vytvoření duplexní federované vlastní vazby pomocí režimu zabezpečení zprávy TCP</span><span class="sxs-lookup"><span data-stu-id="ff341-117">To create a duplex federated custom binding with TCP message security mode</span></span>

1. <span data-ttu-id="ff341-118">V uzlu [\<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) konfiguračního souboru vytvořte prvek [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="ff341-118">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="ff341-119">Uvnitř [\<elementu > CustomBinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) vytvořte [\<vazba >](../../configure-apps/file-schema/wcf/bindings.md) element s atributem `name` nastaveným na `FederationDuplexTcpMessageSecurityBinding`.</span><span class="sxs-lookup"><span data-stu-id="ff341-119">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="ff341-120">Uvnitř [\<vazba >](../../configure-apps/file-schema/wcf/bindings.md) elementu vytvořte [\<element zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) s atributem `authenticationMode` nastaveným na `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="ff341-120">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="ff341-121">Uvnitř prvku [\<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) vytvořte prvek [\<secureConversationBootstrap](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) s atributem `authenticationMode` nastaveným na `IssuedTokenForCertificate` nebo `IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="ff341-121">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="ff341-122">Po elementu [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) vytvořte prázdný prvek [\<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) .</span><span class="sxs-lookup"><span data-stu-id="ff341-122">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a><span data-ttu-id="ff341-123">Vytvoření duplexní federované vlastní vazby se smíšeným režimem zabezpečení TCP</span><span class="sxs-lookup"><span data-stu-id="ff341-123">To create a duplex federated custom binding with TCP mixed security mode</span></span>

1. <span data-ttu-id="ff341-124">V uzlu [\<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) konfiguračního souboru vytvořte prvek [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="ff341-124">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="ff341-125">Uvnitř [\<elementu > CustomBinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) vytvořte [\<vazba >](../../configure-apps/file-schema/wcf/bindings.md) element s atributem `name` nastaveným na `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span><span class="sxs-lookup"><span data-stu-id="ff341-125">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span></span>

3. <span data-ttu-id="ff341-126">Uvnitř [\<vazba >](../../configure-apps/file-schema/wcf/bindings.md) elementu vytvořte [\<element zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) s atributem `authenticationMode` nastaveným na `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="ff341-126">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="ff341-127">Uvnitř prvku [\<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) vytvořte prvek [\<secureConversationBootstrap](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) s atributem `authenticationMode` nastaveným na `IssuedTokenForCertificate` nebo `IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="ff341-127">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="ff341-128">Po elementu [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) vytvořte prázdný prvek [\<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) .</span><span class="sxs-lookup"><span data-stu-id="ff341-128">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span></span>

6. <span data-ttu-id="ff341-129">Po [\<elementu > sslStreamSecurity](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) vytvořte prázdný prvek [\<tcpTransport](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) .</span><span class="sxs-lookup"><span data-stu-id="ff341-129">Following the [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="code-sample"></a><span data-ttu-id="ff341-130">Ukázka kódu</span><span class="sxs-lookup"><span data-stu-id="ff341-130">Code Sample</span></span>

### <a name="sample-with-3-bindings"></a><span data-ttu-id="ff341-131">Ukázka se 3 vazbami</span><span class="sxs-lookup"><span data-stu-id="ff341-131">Sample with 3 Bindings</span></span>

1. <span data-ttu-id="ff341-132">Do konfiguračního souboru vložte následující kód.</span><span class="sxs-lookup"><span data-stu-id="ff341-132">Insert the following code into your configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="ff341-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="ff341-133">Example</span></span>

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
