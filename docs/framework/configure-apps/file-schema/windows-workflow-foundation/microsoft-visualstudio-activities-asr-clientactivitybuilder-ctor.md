---
title: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder... konstruktoru
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
api_name: Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder..ctor
api_location: Microsoft.VisualStudio.Activities.dll
api_type: Assembly
ms.assetid: 6b44b13c-7a23-4df2-8f9f-45e2b1430002
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e8d9e9bfb0967b6c41a3df0015bdd6b4101e0c06
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="microsoftvisualstudioactivitiesasrclientactivitybuilderctor"></a>Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder... konstruktoru
Vytvoří instanci [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md) třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp  
public ClientActivityBuilder(OperationDescription operationDescription, string configurationName, string proxyNamespace);  
```  
  
#### <a name="parameters"></a>Parametry  
  
## <a name="parameter-values"></a>Hodnoty parametru  
 *operationDescription*  
  
 Popisuje operace, která má být provedena v aktivity pracovního postupu, který má být vytvořen, včetně název operace, návratový typ a informace o parametru. Hodnota tohoto parametru nesmí být **null**. Ji by měl popisovat synchronní operaci, která používá zprávy smlouvy a použije argument s jedné zprávy. Nejsou-li tyto podmínky splněny, výsledek modulu runtime pomocí konstruktoru a metod této třídy nejsou definovány.  
  
 *configurationName*  
  
 Určuje název konfigurace koncového bodu. Hodnota tohoto parametru nesmí být buď **null** nebo je prázdný. Nejsou-li tyto podmínky splněny, výsledek modulu runtime pomocí konstruktoru a metod této třídy nejsou definovány.  
  
 *proxyNamespace*  
  
 Určuje obor názvů služby pro operaci. Hodnota tohoto parametru nesmí být buď **null** nebo je prázdný. Nejsou-li tyto podmínky splněny, výsledek modulu runtime pomocí konstruktoru a metod této třídy nejsou definovány.  
  
## <a name="see-also"></a>Viz také  
 [Microsoft.VisualStudio.Activities.Asr.ClientActivityBuilder](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/microsoft-visualstudio-activities-asr-clientactivitybuilder.md)
