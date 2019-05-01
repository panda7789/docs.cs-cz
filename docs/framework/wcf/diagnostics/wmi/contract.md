---
title: Contract1
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: 10789f9a2940c239ae20c8fd1e9d48bca0e820ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963693"
---
# <a name="contract"></a>Kontrakt
Kontrakt  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída smlouvy nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída smlouvy má následující vlastnosti:  
  
### <a name="appdomainid"></a>AppDomainId  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Id domény, která hostuje kontrakt.  
  
### <a name="behaviors"></a>Chování  
 Datový typ: Chování pole  
  
 Typ přístupu: jen pro čtení  
  
 Vlastnosti přičleněné k tomuto kontraktu.  
  
### <a name="name"></a>Název  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Název kontraktu v jazyce WSDL.  
  
### <a name="namespace"></a>Obor názvů  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Obor názvů `portType` elementu v jazyce WSDL.  
  
### <a name="operations"></a>Operace  
 Datový typ: Operace pole  
  
 Typ přístupu: jen pro čtení  
  
 Operace tohoto kontraktu.  
  
### <a name="processid"></a>ID procesu  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Proces Id procesu, který hostuje kontrakt.  
  
### <a name="ref"></a>ref  
 Datový typ: Kontrakt  
  
 Typ přístupu: jen pro čtení  
  
 Typ zpětného volání v případě, že kontrakt je oboustranný.  
  
### <a name="sessionmode"></a>SessionMode  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Určuje, zda kontrakt vyžaduje, aby připojení připojené k tomuto kontraktu použilo kanálové relace.  
  
### <a name="type"></a>Type  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Typ kontraktu.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.ContractDescription>
