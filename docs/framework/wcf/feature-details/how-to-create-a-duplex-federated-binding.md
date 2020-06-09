---
title: 'Postupy: Vytvoření duplexní federované vazby'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: e93651ce9fe9dae55c299fcb061da6bdc4b6bc5e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598967"
---
# <a name="how-to-create-a-duplex-federated-binding"></a><span data-ttu-id="76904-102">Postupy: Vytvoření duplexní federované vazby</span><span class="sxs-lookup"><span data-stu-id="76904-102">How to: Create a Duplex Federated Binding</span></span>

<span data-ttu-id="76904-103"><xref:System.ServiceModel.WSFederationHttpBinding>podporuje pouze kontrakty pro výměnu zpráv datagram a Request/Reply.</span><span class="sxs-lookup"><span data-stu-id="76904-103"><xref:System.ServiceModel.WSFederationHttpBinding> only supports the datagram and request/reply message exchange contracts.</span></span> <span data-ttu-id="76904-104">Pokud chcete použít oboustrannou smlouvu výměny zpráv, musíte vytvořit vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="76904-104">To use the duplex message exchange contract, you must create a custom binding.</span></span> <span data-ttu-id="76904-105">Následující postupy ukazují, jak to provést v konfiguraci, použití zabezpečení režimu zprávy pro přenosy HTTP a TCP a použití smíšeného režimu zabezpečení pro přenos TCP.</span><span class="sxs-lookup"><span data-stu-id="76904-105">The following procedures show how to do this in configuration, using Message mode security for the HTTP and TCP transports, and using mixed mode security for the TCP transport.</span></span> <span data-ttu-id="76904-106">Vzorový kód zobrazující všechny 3 vazby jsou na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="76904-106">Sample code showing all 3 bindings is at the end of this topic.</span></span>

<span data-ttu-id="76904-107">Vazbu můžete vytvořit také v kódu.</span><span class="sxs-lookup"><span data-stu-id="76904-107">You can also create the binding in code.</span></span> <span data-ttu-id="76904-108">Popis prvků vazby, které se mají vytvořit, naleznete v tématu [How to: Create a Custom Binding using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="76904-108">For a description of the binding elements stack to create, see [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a><span data-ttu-id="76904-109">Vytvoření duplexní federované vlastní vazby pomocí protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="76904-109">To create a duplex federated custom binding with HTTP</span></span>

1. <span data-ttu-id="76904-110">V [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) uzlu konfiguračního souboru vytvořte [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="76904-110">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="76904-111">Uvnitř [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) elementu vytvořte [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element s `name` atributem nastaveným na `FederationDuplexHttpMessageSecurityBinding` .</span><span class="sxs-lookup"><span data-stu-id="76904-111">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexHttpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="76904-112">Uvnitř [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elementu vytvořte [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element s `authenticationMode` atributem nastaveným na `SecureConversation` .</span><span class="sxs-lookup"><span data-stu-id="76904-112">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="76904-113">Uvnitř [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elementu vytvořte [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element s `authenticationMode` atributem nastaveným na `IssuedTokenForCertificate` nebo `IssuedTokenForSslNegotiated` .</span><span class="sxs-lookup"><span data-stu-id="76904-113">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="76904-114">Po [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elementu vytvořte prázdný [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) element.</span><span class="sxs-lookup"><span data-stu-id="76904-114">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) element.</span></span>

6. <span data-ttu-id="76904-115">Po [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) elementu vytvořte prázdný [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) element.</span><span class="sxs-lookup"><span data-stu-id="76904-115">Following the [\<compositeDuplex>](../../configure-apps/file-schema/wcf/compositeduplex.md) element, create an empty [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) element.</span></span>

7. <span data-ttu-id="76904-116">Po [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) elementu vytvořte prázdný [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) element.</span><span class="sxs-lookup"><span data-stu-id="76904-116">Following the [\<oneWay>](../../configure-apps/file-schema/wcf/oneway.md) element, create an empty [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a><span data-ttu-id="76904-117">Vytvoření duplexní federované vlastní vazby pomocí režimu zabezpečení zprávy TCP</span><span class="sxs-lookup"><span data-stu-id="76904-117">To create a duplex federated custom binding with TCP message security mode</span></span>

1. <span data-ttu-id="76904-118">V [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) uzlu konfiguračního souboru vytvořte [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="76904-118">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="76904-119">Uvnitř [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) elementu vytvořte [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element s `name` atributem nastaveným na `FederationDuplexTcpMessageSecurityBinding` .</span><span class="sxs-lookup"><span data-stu-id="76904-119">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpMessageSecurityBinding`.</span></span>

3. <span data-ttu-id="76904-120">Uvnitř [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elementu vytvořte [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element s `authenticationMode` atributem nastaveným na `SecureConversation` .</span><span class="sxs-lookup"><span data-stu-id="76904-120">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="76904-121">Uvnitř [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elementu vytvořte [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element s `authenticationMode` atributem nastaveným na `IssuedTokenForCertificate` nebo `IssuedTokenForSslNegotiated` .</span><span class="sxs-lookup"><span data-stu-id="76904-121">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="76904-122">Po [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elementu vytvořte prázdný [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) element.</span><span class="sxs-lookup"><span data-stu-id="76904-122">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a><span data-ttu-id="76904-123">Vytvoření duplexní federované vlastní vazby se smíšeným režimem zabezpečení TCP</span><span class="sxs-lookup"><span data-stu-id="76904-123">To create a duplex federated custom binding with TCP mixed security mode</span></span>

1. <span data-ttu-id="76904-124">V [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) uzlu konfiguračního souboru vytvořte [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="76904-124">In the [\<bindings>](../../configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element.</span></span>

2. <span data-ttu-id="76904-125">Uvnitř [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) elementu vytvořte [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element s `name` atributem nastaveným na `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding` .</span><span class="sxs-lookup"><span data-stu-id="76904-125">Inside the [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element with the `name` attribute set to `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span></span>

3. <span data-ttu-id="76904-126">Uvnitř [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) elementu vytvořte [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element s `authenticationMode` atributem nastaveným na `SecureConversation` .</span><span class="sxs-lookup"><span data-stu-id="76904-126">Inside the [\<binding>](../../configure-apps/file-schema/wcf/bindings.md) element, create a [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>

4. <span data-ttu-id="76904-127">Uvnitř [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elementu vytvořte [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element s `authenticationMode` atributem nastaveným na `IssuedTokenForCertificate` nebo `IssuedTokenForSslNegotiated` .</span><span class="sxs-lookup"><span data-stu-id="76904-127">Inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>

5. <span data-ttu-id="76904-128">Po [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) elementu vytvořte prázdný [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span><span class="sxs-lookup"><span data-stu-id="76904-128">Following the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span></span>

6. <span data-ttu-id="76904-129">Po [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) elementu vytvořte prázdný [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) element.</span><span class="sxs-lookup"><span data-stu-id="76904-129">Following the [\<sslStreamSecurity>](../../configure-apps/file-schema/wcf/sslstreamsecurity.md) element, create an empty [\<tcpTransport>](../../configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>

## <a name="code-sample"></a><span data-ttu-id="76904-130">Ukázka kódu</span><span class="sxs-lookup"><span data-stu-id="76904-130">Code Sample</span></span>

### <a name="sample-with-3-bindings"></a><span data-ttu-id="76904-131">Ukázka se 3 vazbami</span><span class="sxs-lookup"><span data-stu-id="76904-131">Sample with 3 Bindings</span></span>

1. <span data-ttu-id="76904-132">Do konfiguračního souboru vložte následující kód.</span><span class="sxs-lookup"><span data-stu-id="76904-132">Insert the following code into your configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="76904-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="76904-133">Example</span></span>

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
