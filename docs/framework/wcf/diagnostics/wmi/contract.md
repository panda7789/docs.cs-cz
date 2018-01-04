---
title: Contract1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 04a5cb87b9ed61fd278ce0f2e05e5f1c954de5b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="contract"></a>Kontrakt
Kontrakt  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 Třídou kontraktu nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída smlouvy má následující vlastnosti:  
  
### <a name="appdomainid"></a>AppDomainId  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Identifikační číslo domény, která hostuje kontrakt.  
  
### <a name="behaviors"></a>Chování  
 Datový typ: chování pole  
  
 Přístup k typu: jen pro čtení  
  
 Chování přidružené k této smlouvy.  
  
### <a name="name"></a>Název  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Název smlouvy, které ve schématu WSDL.  
  
### <a name="namespace"></a>Obor názvů  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Obor názvů `portType` element v jazyce WSDL.  
  
### <a name="operations"></a>Operace  
 Datový typ: operace pole  
  
 Přístup k typu: jen pro čtení  
  
 Operace tohoto kontraktu.  
  
### <a name="processid"></a>ID procesu  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Id procesu, který je hostitelem kontrakt procesu.  
  
### <a name="ref"></a>ref  
 Datový typ: kontraktu  
  
 Přístup k typu: jen pro čtení  
  
 Typ zpětné volání, když je kontrakt duplexního kontraktu.  
  
### <a name="sessionmode"></a>SessionMode  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Určuje, jestli kontrakt vyžaduje vazby přidružené k této smlouvy pro použití kanálu relací.  
  
### <a name="type"></a>Typ  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Typ smlouvy.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.ContractDescription>
