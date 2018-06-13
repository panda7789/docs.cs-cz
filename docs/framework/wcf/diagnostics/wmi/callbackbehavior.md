---
title: CallbackBehavior
ms.date: 03/30/2017
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
ms.openlocfilehash: 2755ac4f365536366b41e743110ce494063a5ecc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486935"
---
# <a name="callbackbehavior"></a>CallbackBehavior
CallbackBehavior  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class CallbackBehavior : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  boolean MaxItemsInObjectGraph;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída CallbackBehavior nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída CallbackBehavior má následující vlastnosti:  
  
### <a name="automaticsessionshutdown"></a>AutomaticSessionShutdown  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 V případě hodnoty true relace se automaticky zavře po ukončení služby duplexní relace.  
  
### <a name="concurrencymode"></a>Režim ConcurrencyMode  
 Datový typ: řetězec  
Přístup k typu: jen pro čtení  
  
 Určuje, jestli služba podporuje jedno vlákno, více vláken nebo znovu zadaná volání.  
  
### <a name="ignoreextensiondataobject"></a>IgnoreExtensionDataObject  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Hodnota, která určuje, zda chcete odesílat data neznámé serializace drátové síti.  
  
### <a name="includeexceptiondetailinfaults"></a>Třídu IncludeExceptionDetailInFaults  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Když je povolené, podrobnosti o výjimkách odvolání jsou připojené k chybám vrácených ke službě.  
  
### <a name="maxitemsinobjectgraph"></a>maxItemsInObjectGraph  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Maximální počet položek v serializovaný objekt povoleny.  
  
### <a name="usesynchronizationcontext"></a>UseSynchronizationContext  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda chcete použít aktuální kontext synchronizace pro vybrání procesu spuštění.  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda je systém nebo aplikace vynucuje zpracování záhlaví SOAP MustUnderstand.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>
