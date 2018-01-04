---
title: "Postupy: Vytvoření duplexní federované vazby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d40d13ca861cd18cf5f2a72e94d1aca146c2c19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-duplex-federated-binding"></a><span data-ttu-id="bf501-102">Postupy: Vytvoření duplexní federované vazby</span><span class="sxs-lookup"><span data-stu-id="bf501-102">How to: Create a Duplex Federated Binding</span></span>
<span data-ttu-id="bf501-103"><xref:System.ServiceModel.WSFederationHttpBinding>podporuje pouze kontrakty zpráv exchange datagram a požadavek nebo odpověď.</span><span class="sxs-lookup"><span data-stu-id="bf501-103"><xref:System.ServiceModel.WSFederationHttpBinding> only supports the datagram and request/reply message exchange contracts.</span></span> <span data-ttu-id="bf501-104">Pokud chcete použít exchange kontrakt duplexní zprávy, musíte vytvořit vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="bf501-104">To use the duplex message exchange contract, you must create a custom binding.</span></span> <span data-ttu-id="bf501-105">Následující postupy ukazují, jak to udělat v konfiguraci, pomocí režimu zabezpečení zpráv pro přenosy protokolu HTTP a TCP a používá zabezpečení ve smíšeném režimu pro přenos TCP.</span><span class="sxs-lookup"><span data-stu-id="bf501-105">The following procedures show how to do this in configuration, using Message mode security for the HTTP and TCP transports, and using mixed mode security for the TCP transport.</span></span> <span data-ttu-id="bf501-106">Ukázkový kód zobrazuje všechny 3 vazby je na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="bf501-106">Sample code showing all 3 bindings is at the end of this topic.</span></span>  
  
 <span data-ttu-id="bf501-107">Můžete také vytvořit vazby v kódu.</span><span class="sxs-lookup"><span data-stu-id="bf501-107">You can also create the binding in code.</span></span> <span data-ttu-id="bf501-108">Popis zásobníku elementů vazby k vytvoření najdete v tématu [postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="bf501-108">For a description of the binding elements stack to create, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-http"></a><span data-ttu-id="bf501-109">K vytvoření duplexní federované vlastní vazby s protokolem HTTP</span><span class="sxs-lookup"><span data-stu-id="bf501-109">To create a duplex federated custom binding with HTTP</span></span>  
  
1.  <span data-ttu-id="bf501-110">V [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) vytvořit uzel konfiguračního souboru [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="bf501-110">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>  
  
2.  <span data-ttu-id="bf501-111">Uvnitř [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu, vytvoření [ \<vazby >](../../../../docs/framework/misc/binding.md) element s `name` atribut nastaven na `FederationDuplexHttpMessageSecurityBinding`.</span><span class="sxs-lookup"><span data-stu-id="bf501-111">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexHttpMessageSecurityBinding`.</span></span>  
  
3.  <span data-ttu-id="bf501-112">Uvnitř [ \<vazby >](../../../../docs/framework/misc/binding.md) elementu, vytvoření [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element s `authenticationMode` atribut nastaven na `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="bf501-112">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>  
  
4.  <span data-ttu-id="bf501-113">Uvnitř [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, vytvoření [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element s `authenticationMode` atribut nastaven na `IssuedTokenForCertificate` nebo `IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="bf501-113">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>  
  
5.  <span data-ttu-id="bf501-114">Následující [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, vytvořte prázdnou [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element.</span><span class="sxs-lookup"><span data-stu-id="bf501-114">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element.</span></span>  
  
6.  <span data-ttu-id="bf501-115">Následující [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) elementu, vytvořte prázdnou [ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element.</span><span class="sxs-lookup"><span data-stu-id="bf501-115">Following the [\<compositeDuplex>](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) element, create an empty [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element.</span></span>  
  
7.  <span data-ttu-id="bf501-116">Následující [ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) elementu, vytvořte prázdnou [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) element.</span><span class="sxs-lookup"><span data-stu-id="bf501-116">Following the [\<oneWay>](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) element, create an empty [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) element.</span></span>  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a><span data-ttu-id="bf501-117">K vytvoření duplexní federované vlastní vazby s režimem zabezpečení zpráv TCP</span><span class="sxs-lookup"><span data-stu-id="bf501-117">To create a duplex federated custom binding with TCP message security mode</span></span>  
  
1.  <span data-ttu-id="bf501-118">V [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) vytvořit uzel konfiguračního souboru [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="bf501-118">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>   
  
2.  <span data-ttu-id="bf501-119">Uvnitř [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu, vytvoření [ \<vazby >](../../../../docs/framework/misc/binding.md) element s `name` atribut nastaven na `FederationDuplexTcpMessageSecurityBinding`.</span><span class="sxs-lookup"><span data-stu-id="bf501-119">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexTcpMessageSecurityBinding`.</span></span>  
  
3.  <span data-ttu-id="bf501-120">Uvnitř [ \<vazby >](../../../../docs/framework/misc/binding.md) elementu, vytvoření [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element s `authenticationMode` atribut nastaven na `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="bf501-120">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>  
  
4.  <span data-ttu-id="bf501-121">Uvnitř [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, vytvoření [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element s `authenticationMode` atribut nastaven na `IssuedTokenForCertificate` nebo `IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="bf501-121">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>  
  
5.  <span data-ttu-id="bf501-122">Následující [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, vytvořte prázdnou [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span><span class="sxs-lookup"><span data-stu-id="bf501-122">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a><span data-ttu-id="bf501-123">Chcete-li vytvořit duplexní režim federovaný vlastní vazby s TCP zabezpečení smíšený režim</span><span class="sxs-lookup"><span data-stu-id="bf501-123">To create a duplex federated custom binding with TCP mixed security mode</span></span>  
  
1.  <span data-ttu-id="bf501-124">V [ \<vazby >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) vytvořit uzel konfiguračního souboru [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span><span class="sxs-lookup"><span data-stu-id="bf501-124">In the [\<bindings>](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) node of the configuration file, create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element.</span></span>   
  
2.  <span data-ttu-id="bf501-125">Uvnitř [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elementu, vytvoření [ \<vazby >](../../../../docs/framework/misc/binding.md) element s `name` atribut nastaven na `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span><span class="sxs-lookup"><span data-stu-id="bf501-125">Inside the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) element, create a [\<binding>](../../../../docs/framework/misc/binding.md) element with the `name` attribute set to `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.</span></span>  
  
3.  <span data-ttu-id="bf501-126">Uvnitř [ \<vazby >](../../../../docs/framework/misc/binding.md) elementu, vytvoření [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element s `authenticationMode` atribut nastaven na `SecureConversation`.</span><span class="sxs-lookup"><span data-stu-id="bf501-126">Inside the [\<binding>](../../../../docs/framework/misc/binding.md) element, create a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element with the `authenticationMode` attribute set to `SecureConversation`.</span></span>  
  
4.  <span data-ttu-id="bf501-127">Uvnitř [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, vytvoření [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element s `authenticationMode` atribut nastaven na `IssuedTokenForCertificate` nebo `IssuedTokenForSslNegotiated`.</span><span class="sxs-lookup"><span data-stu-id="bf501-127">Inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) element with the `authenticationMode` attribute set to `IssuedTokenForCertificate` or `IssuedTokenForSslNegotiated`.</span></span>  
  
5.  <span data-ttu-id="bf501-128">Následující [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elementu, vytvořte prázdnou [ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span><span class="sxs-lookup"><span data-stu-id="bf501-128">Following the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) element, create an empty [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element.</span></span>  
  
6.  <span data-ttu-id="bf501-129">Následující [ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) elementu, vytvořte prázdnou [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span><span class="sxs-lookup"><span data-stu-id="bf501-129">Following the [\<sslStreamSecurity>](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) element, create an empty [\<tcpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) element.</span></span>  
  
## <a name="code-sample"></a><span data-ttu-id="bf501-130">Ukázka kódu</span><span class="sxs-lookup"><span data-stu-id="bf501-130">Code Sample</span></span>  
  
#### <a name="sample-with-3-bindings"></a><span data-ttu-id="bf501-131">Ukázka s 3 vazby</span><span class="sxs-lookup"><span data-stu-id="bf501-131">Sample with 3 Bindings</span></span>  
  
1.  <span data-ttu-id="bf501-132">Vložte následující kód do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="bf501-132">Insert the following code into your configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf501-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="bf501-133">Example</span></span>  
  
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
