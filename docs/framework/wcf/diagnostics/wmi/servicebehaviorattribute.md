---
title: ServiceBehaviorAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d6b0620e9cb2575bcfe9cd6f01b5d87669df69b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="servicebehaviorattribute"></a>ServiceBehaviorAttribute
ServiceBehaviorAttribute  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class ServiceBehaviorAttribute : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  string ConfigurationName;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  string InstanceContextMode;  
  sint32 MaxItemsInObjectGraph;  
  string Name;  
  string Namespace;  
  boolean ReleaseServiceInstanceOnTransactionComplete;  
  boolean TransactionAutoCompleteOnSessionClose;  
  string TransactionIsolationLevel;  
  datetime TransactionTimeout;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída ServiceBehaviorAttribute nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída ServiceBehaviorAttribute má následující vlastnosti:  
  
### <a name="automaticsessionshutdown"></a>AutomaticSessionShutdown  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Označuje, zda automaticky zavřete relaci, když klient ukončí relaci výstupu.  
  
### <a name="concurrencymode"></a>Režim ConcurrencyMode  
 Datový typ: řetězec  
Přístup k typu: jen pro čtení  
  
 Určuje, zda služba podporuje jedno vlákno, více vláken nebo znovu zadaná volání.  
  
### <a name="configurationname"></a>ConfigurationName  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Název konfigurace služby.  
  
### <a name="ignoreextensiondataobject"></a>ignoreExtensionDataObject  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda chcete odesílat data neznámé serializace drátové síti.  
  
### <a name="includeexceptiondetailinfaults"></a>Třídu IncludeExceptionDetailInFaults  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda mají být zahrnuty informace o spravovaných výjimce podrobností chyb SOAP vrácených klientům pro účely ladění.  
  
### <a name="instancecontextmode"></a>Režim InstanceContextMode  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, kdy vytvořit nový objekt služby.  
  
### <a name="maxitemsinobjectgraph"></a>maxItemsInObjectGraph  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet položek v serializovaný objekt povoleny.  
  
### <a name="name"></a>Název  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Atribut názvu služby v jazyce WSDL.  
  
### <a name="namespace"></a>Obor názvů  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Cílový obor názvů služby v jazyce WSDL.  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a>ReleaseServiceInstanceOnTransactionComplete  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, jestli je objekt služby recykluje po dokončení aktuální transakci.  
  
### <a name="transactionautocompleteonsessionclose"></a>TransactionAutoCompleteOnSessionClose  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda jsou nevyřízené transakce dokončeny zavře aktuální relaci.  
  
### <a name="transactionisolationlevel"></a>TransactionIsolationLevel  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Určuje úroveň izolace transakce.  
  
### <a name="transactiontimeout"></a>Vlastnost TransactionTimeout  
 Datový typ: data a času  
  
 Přístup k typu: jen pro čtení  
  
 Období, ve kterém musíte dokončit transakci.  
  
### <a name="usesynchronizationcontext"></a>UseSynchronizationContext  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda chcete použít aktuální kontext synchronizace zvolit provádění vlákna.  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda je systém nebo aplikace vynucuje zpracování záhlaví SOAP MustUnderstand.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>
