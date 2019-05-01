---
title: CallbackBehavior
ms.date: 03/30/2017
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
ms.openlocfilehash: 9d8f4335c304d164daafeb0ad4de5b4e3bba4590
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963953"
---
# <a name="callbackbehavior"></a>CallbackBehavior
CallbackBehavior  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
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
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 V případě hodnoty true relace je automaticky uzavřena poté, co služba uzavře oboustrannou relaci.  
  
### <a name="concurrencymode"></a>ConcurrencyMode  
 Datový typ: řetězec  
Typ přístupu: jen pro čtení  
  
 Určuje, zda služba podporuje jedno vlákno, několik vláken nebo znovu zadaných volání.  
  
### <a name="ignoreextensiondataobject"></a>IgnoreExtensionDataObject  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Hodnota, která určuje, zda mají data neznámé serializace přenosu.  
  
### <a name="includeexceptiondetailinfaults"></a>Třídu IncludeExceptionDetailInFaults  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Při povolené, podrobnosti o výjimkách odvolání připojeny k chybám vrácených službě.  
  
### <a name="maxitemsinobjectgraph"></a>MaxItemsInObjectGraph  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Maximální počet položek povolených v serializovaném objektu.  
  
### <a name="usesynchronizationcontext"></a>UseSynchronizationContext  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Určuje, jestli se má použít aktuální synchronizační kontext pro výběr vlákna exekuce.  
  
### <a name="validatemustunderstand"></a>ValidateMustUnderstand  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Určuje, zda systém nebo aplikace uplatňuje zpracování záhlaví SOAP MustUnderstand.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.CallbackBehaviorAttribute>
