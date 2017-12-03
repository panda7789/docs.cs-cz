---
title: "WMI – přehled tříd"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b95a51f5-8251-4619-ae05-7de88cb90f9a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7a74f1d7e70b8664df5022d6f9f42cf04b88f930
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="wmi-class-reference"></a><span data-ttu-id="19c69-102">WMI – přehled tříd</span><span class="sxs-lookup"><span data-stu-id="19c69-102">WMI Class Reference</span></span>
<span data-ttu-id="19c69-103">Tato část obsahuje seznam všech tříd WMI vystavené [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] zprostředkovatele rozhraní WMI.</span><span class="sxs-lookup"><span data-stu-id="19c69-103">This section lists all the WMI classes exposed by the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] WMI provider.</span></span>  
  
## <a name="accessing-wmi-instances"></a><span data-ttu-id="19c69-104">Přístup k instance rozhraní WMI</span><span class="sxs-lookup"><span data-stu-id="19c69-104">Accessing WMI Instances</span></span>  
 <span data-ttu-id="19c69-105">Všechny třídy uvedené v odkaz na objekt rozhraní WMI nemůže být přímo vytvořeny instance, s výjimkou služby, AppDomain, kontrakt, ServiceAppDomain, ServiceToEndpointAssociation a koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="19c69-105">All the classes listed in the WMI Object Reference cannot be directly instantiated, except for Service, AppDomain, Contract, ServiceAppDomain, ServiceToEndpointAssociation and Endpoint.</span></span> <span data-ttu-id="19c69-106">Pro přístup k další instance, má přístup k vlastnostem třídy výše uvedených nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="19c69-106">To access other instances, you can access the properties of the previously mentioned top level classes.</span></span> <span data-ttu-id="19c69-107">Například můžete získat přístup k instanci TransportBindingElement z koncového bodu -> instance vazby -> třídy BindingElements.</span><span class="sxs-lookup"><span data-stu-id="19c69-107">For example, you can access the TransportBindingElement instance from the Endpoint instance -> Binding -> BindingElements.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="19c69-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="19c69-108">In This Section</span></span>  
 [<span data-ttu-id="19c69-109">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="19c69-109">ActivityTransfer</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/activitytransfer.md)  
  
 [<span data-ttu-id="19c69-110">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="19c69-110">AppDomainInfo</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md)  
  
 [<span data-ttu-id="19c69-111">AspNetCompatibilityRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="19c69-111">AspNetCompatibilityRequirementsAttribute</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/aspnetcompatibilityrequirementsattribute.md)  
  
 [<span data-ttu-id="19c69-112">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-112">AsymmetricSecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/asymmetricsecuritybindingelement.md)  
  
 <span data-ttu-id="19c69-113">"Chování třída"</span><span class="sxs-lookup"><span data-stu-id="19c69-113">"Behavior class"</span></span>  
  
 [<span data-ttu-id="19c69-114">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-114">BinaryMessageEncodingBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/binarymessageencodingbindingelement.md)  
  
 [<span data-ttu-id="19c69-115">Vazba</span><span class="sxs-lookup"><span data-stu-id="19c69-115">Binding</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/binding.md)  
  
 [<span data-ttu-id="19c69-116">BindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-116">BindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/bindingelement.md)  
  
 [<span data-ttu-id="19c69-117">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="19c69-117">CallbackBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/callbackbehavior.md)  
  
 [<span data-ttu-id="19c69-118">Třída Channel</span><span class="sxs-lookup"><span data-stu-id="19c69-118">Channel class</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/channel-class.md)  
  
 [<span data-ttu-id="19c69-119">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="19c69-119">ChannelPoolSettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/channelpoolsettings.md)  
  
 [<span data-ttu-id="19c69-120">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="19c69-120">ClientCredentials</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/clientcredentials.md)  
  
 [<span data-ttu-id="19c69-121">ClientViaBehavior</span><span class="sxs-lookup"><span data-stu-id="19c69-121">ClientViaBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/clientviabehavior.md)  
  
 [<span data-ttu-id="19c69-122">CompositeDuplexBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-122">CompositeDuplexBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/compositeduplexbindingelement.md)  
  
 [<span data-ttu-id="19c69-123">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-123">ConnectionOrientedTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/connectionorientedtransportbindingelement.md)  
  
 [<span data-ttu-id="19c69-124">Kontrakt</span><span class="sxs-lookup"><span data-stu-id="19c69-124">Contract</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/contract.md)  
  
 [<span data-ttu-id="19c69-125">CustomBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-125">CustomBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/custombindingelement.md)  
  
 [<span data-ttu-id="19c69-126">Atribut DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="19c69-126">DeliveryRequirementsAttribute</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/deliveryrequirementsattribute.md)  
  
 [<span data-ttu-id="19c69-127">Koncový bod</span><span class="sxs-lookup"><span data-stu-id="19c69-127">Endpoint</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md)  
  
 [<span data-ttu-id="19c69-128">HttpsTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-128">HttpsTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/httpstransportbindingelement.md)  
  
 [<span data-ttu-id="19c69-129">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-129">HttpTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/httptransportbindingelement.md)  
  
 [<span data-ttu-id="19c69-130">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="19c69-130">LocalServiceSecuritySettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/localservicesecuritysettings.md)  
  
 [<span data-ttu-id="19c69-131">MatchAllEndpointBehavior</span><span class="sxs-lookup"><span data-stu-id="19c69-131">MatchAllEndpointBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/matchallendpointbehavior.md)  
  
 [<span data-ttu-id="19c69-132">Položka</span><span class="sxs-lookup"><span data-stu-id="19c69-132">MessageEncodingBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/messageencodingbindingelement.md)  
  
 [<span data-ttu-id="19c69-133">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="19c69-133">MsmqBindingElementBase</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/msmqbindingelementbase.md)  
  
 [<span data-ttu-id="19c69-134">MsmqIntegrationBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-134">MsmqIntegrationBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/msmqintegrationbindingelement.md)  
  
 [<span data-ttu-id="19c69-135">Prvkem MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-135">MsmqTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/msmqtransportbindingelement.md)  
  
 [<span data-ttu-id="19c69-136">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-136">MtomMessageEncodingBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/mtommessageencodingbindingelement.md)  
  
 [<span data-ttu-id="19c69-137">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="19c69-137">MustUnderstandBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/mustunderstandbehavior.md)  
  
 [<span data-ttu-id="19c69-138">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="19c69-138">NamedPipeConnectionPoolSettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/namedpipeconnectionpoolsettings.md)  
  
 [<span data-ttu-id="19c69-139">NamedPipeTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-139">NamedPipeTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/namedpipetransportbindingelement.md)  
  
 [<span data-ttu-id="19c69-140">Třída OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-140">OneWayBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/onewaybindingelement.md)  
  
 <span data-ttu-id="19c69-141">"Třída operation"</span><span class="sxs-lookup"><span data-stu-id="19c69-141">"Operation class"</span></span>  
  
 [<span data-ttu-id="19c69-142">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="19c69-142">OperationBehaviorAttribute</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/operationbehaviorattribute.md)  
  
 [<span data-ttu-id="19c69-143">Tříd PeerCustomResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-143">PeerCustomResolverBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/peercustomresolverbindingelement.md)  
  
 [<span data-ttu-id="19c69-144">Třída PeerResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-144">PeerResolverBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/peerresolverbindingelement.md)  
  
 [<span data-ttu-id="19c69-145">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="19c69-145">PeerSecuritySettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/peersecuritysettings.md)  
  
 [<span data-ttu-id="19c69-146">PeerTransportBindingElement.</span><span class="sxs-lookup"><span data-stu-id="19c69-146">PeerTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/peertransportbindingelement.md)  
  
 [<span data-ttu-id="19c69-147">Třída PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="19c69-147">PeerTransportSecuritySettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/peertransportsecuritysettings.md)  
  
 [<span data-ttu-id="19c69-148">PnrpPeerResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-148">PnrpPeerResolverBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/pnrppeerresolverbindingelement.md)  
  
 [<span data-ttu-id="19c69-149">PrivacyNoticeBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-149">PrivacyNoticeBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/privacynoticebindingelement.md)  
  
 [<span data-ttu-id="19c69-150">Prvek ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-150">ReliableSessionBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/reliablesessionbindingelement.md)  
  
 [<span data-ttu-id="19c69-151">Elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-151">SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/securitybindingelement.md)  
  
 [<span data-ttu-id="19c69-152">Služby</span><span class="sxs-lookup"><span data-stu-id="19c69-152">Service</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/service.md)  
  
 [<span data-ttu-id="19c69-153">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="19c69-153">ServiceAppDomain</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/serviceappdomain.md)  
  
 [<span data-ttu-id="19c69-154">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="19c69-154">ServiceAuthorizationBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/serviceauthorizationbehavior.md)  
  
 [<span data-ttu-id="19c69-155">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="19c69-155">ServiceBehaviorAttribute</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicebehaviorattribute.md)  
  
 [<span data-ttu-id="19c69-156">– ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="19c69-156">ServiceCredentials</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicecredentials.md)  
  
 [<span data-ttu-id="19c69-157">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="19c69-157">ServiceDebugBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicedebugbehavior.md)  
  
 [<span data-ttu-id="19c69-158">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="19c69-158">ServiceMetadataBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicemetadatabehavior.md)  
  
 [<span data-ttu-id="19c69-159">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="19c69-159">ServiceSecurityAuditBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicesecurityauditbehavior.md)  
  
 [<span data-ttu-id="19c69-160">Třídy ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="19c69-160">ServiceThrottlingBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicethrottlingbehavior.md)  
  
 [<span data-ttu-id="19c69-161">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="19c69-161">ServiceTimeoutsBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicetimeoutsbehavior.md)  
  
 [<span data-ttu-id="19c69-162">ServiceToEndpointAssociation</span><span class="sxs-lookup"><span data-stu-id="19c69-162">ServiceToEndpointAssociation</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/servicetoendpointassociation.md)  
  
 [<span data-ttu-id="19c69-163">SslStreamSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-163">SslStreamSecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/sslstreamsecuritybindingelement.md)  
  
 [<span data-ttu-id="19c69-164">Prvek SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-164">SymmetricSecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/symmetricsecuritybindingelement.md)  
  
 [<span data-ttu-id="19c69-165">SynchronousReceiveBehavior</span><span class="sxs-lookup"><span data-stu-id="19c69-165">SynchronousReceiveBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/synchronousreceivebehavior.md)  
  
 [<span data-ttu-id="19c69-166">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="19c69-166">TcpConnectionPoolSettings</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/tcpconnectionpoolsettings.md)  
  
 [<span data-ttu-id="19c69-167">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-167">TcpTransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/tcptransportbindingelement.md)  
  
 [<span data-ttu-id="19c69-168">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-168">TextMessageEncodingBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/textmessageencodingbindingelement.md)  
  
 [<span data-ttu-id="19c69-169">TraceListener</span><span class="sxs-lookup"><span data-stu-id="19c69-169">TraceListener</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/tracelistener.md)  
  
 [<span data-ttu-id="19c69-170">TraceListenerArgument</span><span class="sxs-lookup"><span data-stu-id="19c69-170">TraceListenerArgument</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/tracelistenerargument.md)  
  
 [<span data-ttu-id="19c69-171">TransactedBatchingBehavior</span><span class="sxs-lookup"><span data-stu-id="19c69-171">TransactedBatchingBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/transactedbatchingbehavior.md)  
  
 [<span data-ttu-id="19c69-172">TransactionFlowAttribute</span><span class="sxs-lookup"><span data-stu-id="19c69-172">TransactionFlowAttribute</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/transactionflowattribute.md)  
  
 [<span data-ttu-id="19c69-173">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-173">TransactionFlowBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/transactionflowbindingelement.md)  
  
 [<span data-ttu-id="19c69-174">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-174">TransportBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/transportbindingelement.md)  
  
 [<span data-ttu-id="19c69-175">TransportSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-175">TransportSecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/transportsecuritybindingelement.md)  
  
 [<span data-ttu-id="19c69-176">UseManagedPresentationBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-176">UseManagedPresentationBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/usemanagedpresentationbindingelement.md)  
  
 [<span data-ttu-id="19c69-177">WindowsStreamSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="19c69-177">WindowsStreamSecurityBindingElement</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/windowsstreamsecuritybindingelement.md)  
  
 [<span data-ttu-id="19c69-178">WSAT_TraceEvent</span><span class="sxs-lookup"><span data-stu-id="19c69-178">WSAT_TraceEvent</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/wsat-traceevent.md)  
  
 [<span data-ttu-id="19c69-179">WSAT_TraceProvider</span><span class="sxs-lookup"><span data-stu-id="19c69-179">WSAT_TraceProvider</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/wsat-traceprovider.md)  
  
 [<span data-ttu-id="19c69-180">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="19c69-180">WSAT_TraceRecord</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/wsat-tracerecord.md)  
  
 [<span data-ttu-id="19c69-181">XmlDictionaryReaderQuotas, který</span><span class="sxs-lookup"><span data-stu-id="19c69-181">XmlDictionaryReaderQuotas</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/xmldictionaryreaderquotas.md)  
  
 [<span data-ttu-id="19c69-182">XmlSerializerOperationBehavior</span><span class="sxs-lookup"><span data-stu-id="19c69-182">XmlSerializerOperationBehavior</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/xmlserializeroperationbehavior.md)
