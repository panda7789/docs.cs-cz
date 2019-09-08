---
title: WMI – přehled tříd
ms.date: 03/30/2017
ms.assetid: b95a51f5-8251-4619-ae05-7de88cb90f9a
ms.openlocfilehash: 226e4dedecd152f3a3d4143280529c7823339932
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795883"
---
# <a name="wmi-class-reference"></a>WMI – přehled tříd
V této části jsou uvedené všechny třídy služby WMI vystavené poskytovatelem WMI služby Windows Communication Foundation (WCF).  
  
## <a name="accessing-wmi-instances"></a>Přístup k instancím služby WMI  
 U všech tříd uvedených v odkazu na objekt WMI nelze vytvořit instanci přímo, s výjimkou služby, domény AppDomain, kontraktu, ServiceAppDomain, ServiceToEndpointAssociation a koncového bodu. Chcete-li získat přístup k dalším instancím, můžete získat přístup k vlastnostem dříve uvedených tříd nejvyšší úrovně. Můžete například získat přístup k instanci třídy TransportBindingElement z instance koncového bodu – > vazeb-> BindingElements.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [ActivityTransfer](activitytransfer.md)  
  
 [AppDomainInfo](appdomaininfo.md)  
  
 [AspNetCompatibilityRequirementsAttribute](aspnetcompatibilityrequirementsattribute.md)  
  
 [AsymmetricSecurityBindingElement](asymmetricsecuritybindingelement.md)  
  
 "Třída chování"  
  
 [BinaryMessageEncodingBindingElement](binarymessageencodingbindingelement.md)  
  
 [Binding](binding.md)  
  
 [BindingElement](bindingelement.md)  
  
 [CallbackBehavior](callbackbehavior.md)  
  
 [Channel – třída](channel-class.md)  
  
 [ChannelPoolSettings](channelpoolsettings.md)  
  
 [ClientCredentials](clientcredentials.md)  
  
 [ClientViaBehavior](clientviabehavior.md)  
  
 [CompositeDuplexBindingElement](compositeduplexbindingelement.md)  
  
 [ConnectionOrientedTransportBindingElement](connectionorientedtransportbindingelement.md)  
  
 [Contract](contract.md)  
  
 [CustomBindingElement](custombindingelement.md)  
  
 [DeliveryRequirementsAttribute](deliveryrequirementsattribute.md)  
  
 [Endpoint](endpoint.md)  
  
 [HttpsTransportBindingElement](httpstransportbindingelement.md)  
  
 [HttpTransportBindingElement](httptransportbindingelement.md)  
  
 [LocalServiceSecuritySettings](localservicesecuritysettings.md)  
  
 [MatchAllEndpointBehavior](matchallendpointbehavior.md)  
  
 [MessageEncodingBindingElement](messageencodingbindingelement.md)  
  
 [MsmqBindingElementBase](msmqbindingelementbase.md)  
  
 [MsmqIntegrationBindingElement](msmqintegrationbindingelement.md)  
  
 [MsmqTransportBindingElement](msmqtransportbindingelement.md)  
  
 [MtomMessageEncodingBindingElement](mtommessageencodingbindingelement.md)  
  
 [MustUnderstandBehavior](mustunderstandbehavior.md)  
  
 [NamedPipeConnectionPoolSettings](namedpipeconnectionpoolsettings.md)  
  
 [NamedPipeTransportBindingElement](namedpipetransportbindingelement.md)  
  
 [OneWayBindingElement](onewaybindingelement.md)  
  
 "Třída Operation"  
  
 [OperationBehaviorAttribute](operationbehaviorattribute.md)  
  
 [PeerCustomResolverBindingElement](peercustomresolverbindingelement.md)  
  
 [PeerResolverBindingElement](peerresolverbindingelement.md)  
  
 [PeerSecuritySettings](peersecuritysettings.md)  
  
 [PeerTransportBindingElement](peertransportbindingelement.md)  
  
 [PeerTransportSecuritySettings](peertransportsecuritysettings.md)  
  
 [PnrpPeerResolverBindingElement](pnrppeerresolverbindingelement.md)  
  
 [PrivacyNoticeBindingElement](privacynoticebindingelement.md)  
  
 [ReliableSessionBindingElement](reliablesessionbindingelement.md)  
  
 [SecurityBindingElement](securitybindingelement.md)  
  
 [Service](service.md)  
  
 [ServiceAppDomain](serviceappdomain.md)  
  
 [ServiceAuthorizationBehavior](serviceauthorizationbehavior.md)  
  
 [ServiceBehaviorAttribute](servicebehaviorattribute.md)  
  
 [ServiceCredentials](servicecredentials.md)  
  
 [ServiceDebugBehavior](servicedebugbehavior.md)  
  
 [ServiceMetadataBehavior](servicemetadatabehavior.md)  
  
 [ServiceSecurityAuditBehavior](servicesecurityauditbehavior.md)  
  
 [ServiceThrottlingBehavior](servicethrottlingbehavior.md)  
  
 [ServiceTimeoutsBehavior](servicetimeoutsbehavior.md)  
  
 [ServiceToEndpointAssociation](servicetoendpointassociation.md)  
  
 [SslStreamSecurityBindingElement](sslstreamsecuritybindingelement.md)  
  
 [SymmetricSecurityBindingElement](symmetricsecuritybindingelement.md)  
  
 [SynchronousReceiveBehavior](synchronousreceivebehavior.md)  
  
 [TcpConnectionPoolSettings](tcpconnectionpoolsettings.md)  
  
 [TcpTransportBindingElement](tcptransportbindingelement.md)  
  
 [TextMessageEncodingBindingElement](textmessageencodingbindingelement.md)  
  
 [TraceListener](tracelistener.md)  
  
 [TraceListenerArgument](tracelistenerargument.md)  
  
 [TransactedBatchingBehavior](transactedbatchingbehavior.md)  
  
 [TransactionFlowAttribute](transactionflowattribute.md)  
  
 [TransactionFlowBindingElement](transactionflowbindingelement.md)  
  
 [TransportBindingElement](transportbindingelement.md)  
  
 [TransportSecurityBindingElement](transportsecuritybindingelement.md)  
  
 [UseManagedPresentationBindingElement](usemanagedpresentationbindingelement.md)  
  
 [WindowsStreamSecurityBindingElement](windowsstreamsecuritybindingelement.md)  
  
 [WSAT_TraceEvent](wsat-traceevent.md)  
  
 [WSAT_TraceProvider](wsat-traceprovider.md)  
  
 [WSAT_TraceRecord](wsat-tracerecord.md)  
  
 [XmlDictionaryReaderQuotas](xmldictionaryreaderquotas.md)  
  
 [XmlSerializerOperationBehavior](xmlserializeroperationbehavior.md)
