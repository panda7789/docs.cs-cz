---
title: Třída Operation
ms.date: 03/30/2017
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
ms.openlocfilehash: d9256915afe9fdb8e4c91d186131fe41a7094c56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="operation-class"></a>Třída Operation
Operace  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class Operation  
{  
  string Action;  
  boolean AsyncPattern;  
  Behavior Behaviors[];  
  boolean IsCallback;  
  boolean IsInitiating;  
  boolean IsOneWay;  
  boolean IsTerminating;  
  string MethodSignature;  
  string Name;  
  string ParameterTypes[];  
  string ReplyAction;  
  string ReturnType;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída Operation nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída Operation má následující vlastnosti:  
  
### <a name="action"></a>Akce  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Akce WS-Addressing zprávy požadavku.  
  
### <a name="asyncpattern"></a>Parametru AsyncPattern  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Označuje, že operace je implementovaná asynchronně pomocí `Begin`[otevření nebo uzavření lomené závorky] a `End`pár – metoda [otevření nebo uzavření lomené závorky] v kontraktu služby.  
  
### <a name="behaviors"></a>Chování  
 Datový typ: chování pole  
  
 Přístup k typu: jen pro čtení  
  
 Chování, které jsou spojené s touto operací.  
  
### <a name="iscallback"></a>IsCallback  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Hodnota TRUE, po operaci zpětného volání operace.  
  
### <a name="isinitiating"></a>IsInitiating  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda metoda provádí operaci, která můžete zahájit relaci na serveru.  
  
### <a name="isoneway"></a>IsOneWay  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda operace vrátí zprávu odpovědi.  
  
### <a name="isterminating"></a>IsTerminating  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, zda operace vrátí zprávu odpovědi.  
  
### <a name="methodsignature"></a>MethodSignature  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Podpis metody operace.  
  
### <a name="name"></a>Název  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Název operace.  
  
### <a name="parametertypes"></a>ParameterTypes  
 Datový typ: pole řetězců  
  
 Přístup k typu: jen pro čtení  
  
 Typy parametrů operace.  
  
### <a name="replyaction"></a>ReplyAction  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Hodnota akce SOAP zprávy s odpovědí operace.  
  
### <a name="returntype"></a>Vlastnost ReturnType  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Návratový typ operace.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.OperationDescription>
