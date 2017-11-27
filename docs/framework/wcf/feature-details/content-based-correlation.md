---
title: "Korelace na základě obsahu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f46a2b68-8d24-4122-bbee-9573fc3f9fb4
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: dda6e063744b8a745c5f4be576344ff2823de267
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="content-based-correlation"></a>Korelace na základě obsahu
Když pracovní postup služby komunikaci s klienty a další služby, je často některá data v výměně zpráv, který jednoznačně zpráva má vztah k určité instance. Korelace na základě obsahu používá tato data ve zprávě, jako je například číslo nebo pořadí ID zákazníka, pro směrování zpráv do instance správné pracovního postupu. Toto téma vysvětluje, jak používat korelace na základě obsahu v pracovních postupech.  
  
## <a name="using-content-based-correlation"></a>Pomocí korelace na základě obsahu  
 Korelace na základě obsahu se používá, když pracovní postup služby má několik metod, které jsou dostupné přes jednoho klienta a část dat v výměně zpráv určuje požadovanou instanci.  
  
> [!NOTE]
>  Korelace na základě obsahu je užitečné, když korelace kontextu nelze použít, protože vazba není jedním z podporovaných kontext vazby exchange. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]korelace kontextu, najdete v části [kontextová výměna](../../../../docs/framework/wcf/feature-details/context-exchange-correlation.md).  
  
 Každá zasílání zpráv aktivita používá v tyto komunikace musíte zadat umístění dat ve zprávě, která jednoznačně identifikuje instanci. To se provádí zadáním <xref:System.ServiceModel.MessageQuerySet>, buď pomocí <xref:System.ServiceModel.Activities.QueryCorrelationInitializer> nebo <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A>, který dotazuje zprávu pro část nebo kusy data, která jednoznačně instance.  
  
> [!WARNING]
>  Data, která se používá k identifikaci instance je algoritmus hash, do klíče korelace. Dbát musí zajistit, že data pro korelačního jedinečné, jinak může dojít a způsobit zpráv, které mají být nesprávně směrovanými kolizí v klíči hash. Například existuje korelace zakládá výhradně na jménu zákazníka mohou způsobit kolize, protože může být více zákazníků se stejným názvem. Dvojtečkou (`:`) nesmí být použity jako součást dat použít ke korelaci zprávu, protože se již používá pro vymezení klíč a hodnotu a vytvořit řetězec, který je následně rozdělí dotazu zprávu.  
  
 V následujícím příkladu, počáteční <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> ve službě pracovní postup vrátí `OrderId`, který byl následně předán zpět klientem při volání těchto <xref:System.ServiceModel.Activities.Receive> aktivity v rámci služby pracovního postupu.  
  
 [!code-csharp[CFX_ContentCorrelation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#1)]  
  
 Ukazuje předchozí příklad korelace na základě obsahu, který se inicializuje pomocí <xref:System.ServiceModel.Activities.SendReply>. <xref:System.ServiceModel.MessageQuerySet> Určuje, že se data použít k identifikaci následné zprávy a pokuste se tato služba `OrderId`.  
  
 [!code-csharp[CFX_ContentCorrelation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#2)]  
  
 <xref:System.ServiceModel.Activities.Receive> Aktivitě, která následuje <xref:System.ServiceModel.Activities.SendReply> v pracovním postupu následuje korelace, který byl inicializován nástrojem <xref:System.ServiceModel.Activities.SendReply>. Obě aktivity sdílejí stejné <xref:System.ServiceModel.Activities.CorrelationHandle>, ale každé z nich má svou vlastní <xref:System.ServiceModel.MessageQuerySet> a <xref:System.ServiceModel.XPathMessageQuery> určující, kde je identifikace data v této konkrétní zprávě. Na aktivitu, která inicializuje korelace to <xref:System.ServiceModel.MessageQuerySet> je uveden v <xref:System.ServiceModel.Activities.Receive.CorrelationInitializers%2A> vlastnost a pro všechny následující <xref:System.ServiceModel.Activities.Receive> aktivity, je zadán pomocí <xref:System.ServiceModel.Activities.Receive.CorrelatesOn%2A> vlastnost.  
  
 [!code-csharp[CFX_ContentCorrelation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#3)]  
  
 Existuje korelace na základě obsahu můžete inicializovat pomocí všechny aktivity zasílání zpráv (<xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.ReceiveReply>) při tok dat v rámci zprávy. Pokud jako součást zprávu nepostupuje konkrétním dat, pak může být inicializována explicitně pomocí <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivity. Pokud data na více místech jsou potřeba k jednoznačné identifikaci zprávy, pak lze přidat více dotazů <xref:System.ServiceModel.MessageQuerySet>. V těchto příkladech <xref:System.ServiceModel.Activities.CorrelationHandle> explicitně zadaná pro všechny aktivity pomocí `CorrelatesWith` nebo `CorrelationHandle` vlastnosti, ale pokud existuje jenom jedna korelace požadované pro celý pracovní postup, například v tomto příkladu kde všechno korelaci na `OrderId`, správu popisovač implicitní korelace poskytované <xref:System.ServiceModel.Activities.WorkflowServiceHost> je dostačující.  
  
## <a name="using-the-initializecorrelation-activity"></a>Pomocí aktivity InitializeCorrelation  
 V předchozím příkladu `OrderId` plynoucích volajícího prostřednictvím <xref:System.ServiceModel.Activities.SendReply> aktivitu a to je, kde byl inicializován korelaci. Stejné chování se dá udělat pomocí <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivity. <xref:System.ServiceModel.Activities.InitializeCorrelation> Trvá aktivity <xref:System.ServiceModel.Activities.CorrelationHandle> a slovník položek, které představují data použít k mapování zprávy na správnou instanci. Použít <xref:System.ServiceModel.Activities.InitializeCorrelation> odebrat aktivitu v předchozím příkladu <xref:System.ServiceModel.Activities.SendReply.CorrelationInitializers%2A> z <xref:System.ServiceModel.Activities.SendReply> aktivity a inicializovat pomocí korelace <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivity.  
  
 [!code-csharp[CFX_ContentCorrelation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#4)]  
  
 <xref:System.ServiceModel.Activities.InitializeCorrelation> Aktivita se pak používá v pracovním postupu po proměnné, které mají data jsou naplněny ale předtím, než <xref:System.ServiceModel.Activities.Receive> aktivity, které koreluje s inicializovaná <xref:System.ServiceModel.Activities.CorrelationHandle>.  
  
 [!code-csharp[CFX_ContentCorrelation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#5)]  
  
## <a name="configuring-xpath-queries-using-the-workflow-designer"></a>Konfigurace dotazů XPath pomocí návrháře pracovních postupů  
 V předchozích příkladech aktivity a dotazy jazyka XPath používají v dotazech zpráv byly zadány v kódu. Návrhář postupu provádění v [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] také nabízí možnost k vygenerování výrazů XPath z `DataContract` typy pro korelace na základě obsahu. První výraz XPath nakonfigurované v předchozím příkladu byl nakonfigurován na <xref:System.ServiceModel.Activities.SendReply>.  
  
 [!code-csharp[CFX_ContentCorrelation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#2)]  
  
 Pokud chcete konfigurovat cestu XPath pro zasílání zpráv aktivity v Návrháři pracovních postupů, vyberte aktivitu v Návrháři pracovních postupů. Pokud aktivita je inicializace korelace, jako v předchozím příkladu, klikněte na tlačítko se třemi tečkami pro **CorrelationInitializers** vlastnost **vlastnosti** okno. Zobrazí se **přidat inicializátory korelace** dialogového okna. Z tohoto dialogového okna můžete zadat typ korelace a vyberte obsah, který slouží pro korelaci. <xref:System.ServiceModel.Activities.CorrelationHandle> Proměnná zadaná v **přidat inicializátoru** pole a korelace typu a data pro korelaci je vybraný **dotazů XPath** části dialogového okna.  
  
 ![Dialogové okno CorrelationInitializer](../../../../docs/framework/wcf/feature-details/media/correlationinitializerdlg.jpg "CorrelationInitializerDlg")  
  
 Druhý dotaz XPath v předchozím příkladu jste nakonfigurovali v <xref:System.ServiceModel.Activities.Receive> aktivity.  
  
 [!code-csharp[CFX_ContentCorrelation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_contentcorrelation/cs/program.cs#3)]  
  
 Pokud chcete nakonfigurovat dotaz XPath pro zasílání zpráv aktivity, která se neinicializuje korelaci, vyberte aktivitu v Návrháři pracovních postupů a pak klikněte na tlačítko se třemi tečkami pro **CorrelatesOn** vlastnost v  **Vlastnosti** okno. Zobrazí se **CorrelatesOn definice** dialogového okna.  
  
 ![Definice CorrelatesOn](../../../../docs/framework/wcf/feature-details/media/correlatesondialog.jpg "CorrelatesOnDialog")  
  
 Z tohoto dialogového okna zadejte <xref:System.ServiceModel.Activities.CorrelationHandle> a vyberte položky v **dotazů XPath** seznamu k vytvoření dotazu XPath.
