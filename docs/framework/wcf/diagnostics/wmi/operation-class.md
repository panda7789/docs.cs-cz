---
title: Třída Operation
ms.date: 03/30/2017
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
ms.openlocfilehash: 9696a7f026e54afacb5ccbfa8703a2ba617a9f3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59973197"
---
# <a name="operation-class"></a>Třída Operation
Operace  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
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
  
 Typ přístupu: jen pro čtení  
  
 Akce WS-Adressing zprávy s požadavkem.  
  
### <a name="asyncpattern"></a>AsyncPattern  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Označuje, že operace je provedena asynchronně pomocí `Begin`[otevřít nebo zavřít ostrých závorek] a `End`dvojice metody [otevřít nebo zavřít ostrých závorek] v kontraktu služby.  
  
### <a name="behaviors"></a>Chování  
 Datový typ: Chování pole  
  
 Typ přístupu: jen pro čtení  
  
 Chování, které jsou spojené s touto operací.  
  
### <a name="iscallback"></a>IsCallback  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Hodnota TRUE, pokud je operace operací zpětného volání.  
  
### <a name="isinitiating"></a>IsInitiating  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Určuje, zda metoda provádí operaci, která může iniciovat relaci na serveru.  
  
### <a name="isoneway"></a>IsOneWay  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Určuje, zda operace vrátí zprávy s odpovědí.  
  
### <a name="isterminating"></a>IsTerminating  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Určuje, zda operace vrátí zprávy s odpovědí.  
  
### <a name="methodsignature"></a>MethodSignature  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Označení metody operace.  
  
### <a name="name"></a>Název  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Název operace.  
  
### <a name="parametertypes"></a>ParameterTypes  
 Datový typ: pole řetězců  
  
 Typ přístupu: jen pro čtení  
  
 Typy parametrů operace.  
  
### <a name="replyaction"></a>Třídu ReplyAction  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Hodnota akce SOAP pro odpověď operace.  
  
### <a name="returntype"></a>Vlastnost ReturnType  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Návratový typ operace.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.OperationDescription>
