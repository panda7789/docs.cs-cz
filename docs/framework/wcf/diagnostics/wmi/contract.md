---
title: Kontrakt
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: e4a21e95a6f1f1860ed36c968d17bb8ac8465dce
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868436"
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
 Třída kontraktu nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída kontraktu má následující vlastnosti:  
  
### <a name="appdomainid"></a>AppDomainId  
 Datový typ: sint32  
  
 Typ přístupu: Jen pro čtení  
  
 ID domény AppDomain, která hostuje kontrakt.  
  
### <a name="behaviors"></a>Chování  
 Datový typ: Pole chování  
  
 Typ přístupu: Jen pro čtení  
  
 Chování spojené s touto smlouvou.  
  
### <a name="name"></a>Name  
 Datový typ: řetězec  
  
 Typ přístupu: Jen pro čtení  
  
 Název kontraktu v jazyce WSDL.  
  
### <a name="namespace"></a>Obor názvů  
 Datový typ: řetězec  
  
 Typ přístupu: Jen pro čtení  
  
 Obor názvů `portType` prvku v jazyce WSDL.  
  
### <a name="operations"></a>Operace  
 Datový typ: Pole operace  
  
 Typ přístupu: Jen pro čtení  
  
 Operace tohoto kontraktu.  
  
### <a name="processid"></a>ID procesu  
 Datový typ: sint32  
  
 Typ přístupu: Jen pro čtení  
  
 ID procesu, který hostuje kontrakt.  
  
### <a name="ref"></a>ref  
 Datový typ: Kontrakt  
  
 Typ přístupu: Jen pro čtení  
  
 Typ zpětného volání v případě, že kontrakt je oboustranný.  
  
### <a name="sessionmode"></a>SessionMode  
 Datový typ: řetězec  
  
 Typ přístupu: Jen pro čtení  
  
 Určuje, zda kontrakt vyžaduje, aby vazba přidružená k tomuto kontraktu použila relace kanálu.  
  
### <a name="type"></a>type  
 Datový typ: řetězec  
  
 Typ přístupu: Jen pro čtení  
  
 Typ kontraktu.  
  
## <a name="requirements"></a>Požadavky  
  
|TVOŘÍCÍ|Deklarováno v souboru ServiceModel. mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definováno v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.ContractDescription>
