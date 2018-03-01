---
title: "Rozšiřitelné objekty"
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
helpviewer_keywords:
- extensible objects [WCF]
ms.assetid: bc88cefc-31fb-428e-9447-6d20a7d452af
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a1bb341d9e164b1ce232f238f8ddf4a0cf807363
ms.sourcegitcommit: c1904b0437605a90e5aa65b4abd7e048000e349d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2018
---
# <a name="extensible-objects"></a>Rozšiřitelné objekty
Vzor extensible objektu se používá buď rozšířit existující třídy runtime s novými funkcemi nebo přidat nový stav na objekt. Rozšíření, které jsou připojené k jednomu rozšiřitelné objekty, aktivujte velmi různých fází zpracování pro přístup k sdílení stavu a funkce, které jsou připojené k běžné extensible objekt, který bude mít přístup k chování.  
  
## <a name="the-iextensibleobjectt-pattern"></a>IExtensibleObject\<T > vzor  
 Existují tři rozhraní ve vzoru extensible objektu: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, a <xref:System.ServiceModel.IExtensionCollection%601>.  
  
 <xref:System.ServiceModel.IExtensibleObject%601> Rozhraní je implementováno modulem typy, které umožňují <xref:System.ServiceModel.IExtension%601> objekty, které chcete přizpůsobit jejich funkce.  
  
 Rozšiřitelné objekty povolit dynamické agregace <xref:System.ServiceModel.IExtension%601> objekty. <xref:System.ServiceModel.IExtension%601>objekty jsou charakteristické následující rozhraní:  
  
```  
public interface IExtension<T>  
where T : IExtensibleObject<T>  
{  
    void Attach(T owner);  
    void Detach(T owner);  
}  
```  
  
 Omezení typu zaručuje, že rozšíření může být definovaný jenom pro třídy, které jsou <xref:System.ServiceModel.IExtensibleObject%601>. <xref:System.ServiceModel.IExtension%601.Attach%2A>a <xref:System.ServiceModel.IExtension%601.Detach%2A> poskytnout oznámení o agregace nebo členění.  
  
 Je platná pro implementace omezit, když se může přidat nebo odebrat z vlastníka. Například můžete zcela, zakáže odebrání zákaz přidávání nebo odebírání rozšíření, když jsou vlastníka nebo rozšíření v určitých stavu, zakáže přidávání do několika vlastníky souběžně nebo Povolit jenom jeden přidání následuje jeden odebrat.  
  
 <xref:System.ServiceModel.IExtension%601>všechny interakce s další standardní spravovaná rozhraní není určeno. Konkrétně <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> metoda objektu vlastníka není odpojit normálně jejich rozšíření.  
  
 Při přidání rozšíření do kolekce, <xref:System.ServiceModel.IExtension%601.Attach%2A> je volána před přejde do kolekce. Pokud rozšíření je odebrán z kolekce, <xref:System.ServiceModel.IExtension%601.Detach%2A> je volána po jejím odebrání. To znamená (za předpokladu, že příslušné synchronizace) rozšíření Dal spočítat na nalezené pouze v kolekci bude během je mezi <xref:System.ServiceModel.IExtension%601.Attach%2A> a <xref:System.ServiceModel.IExtension%601.Detach%2A>.  
  
 Předaný objekt <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> nebo <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> nemusí být <xref:System.ServiceModel.IExtension%601> (například můžete předat libovolný objekt), ale je vrácená rozšíření <xref:System.ServiceModel.IExtension%601>.  
  
 Pokud je bez přípony v kolekci <xref:System.ServiceModel.IExtension%601>, <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> , vrátí hodnotu null, a <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> vrátí prázdnou kolekci. Pokud se několik rozšíření implementovat <xref:System.ServiceModel.IExtension%601>, <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> vrátí jeden z nich. Hodnota vrácená z <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> je snímek.
  
 Existují dva základní scénáře. První scénář se používá <xref:System.ServiceModel.IExtensibleObject%601.Extensions%2A> vlastnost jako slovník na základě typu vložení stavu objektu povolení jiné součásti a vyhledejte ho pomocí daného typu.  
  
 Druhý scénář se používá <xref:System.ServiceModel.IExtension%601.Attach%2A> a <xref:System.ServiceModel.IExtension%601.Detach%2A> vlastnosti, které chcete povolit objekt zapojit se do vlastní chování, jako je registrace pro události, sledování přechodů mezi stavy a tak dále.  
  
 <xref:System.ServiceModel.IExtensionCollection%601> Rozhraní je kolekce <xref:System.ServiceModel.IExtension%601> objekty, které umožňují pro načítání <xref:System.ServiceModel.IExtension%601> podle jeho typu. <xref:System.ServiceModel.IExtensionCollection%601.Find%2A?displayProperty=nameWithType>Vrátí naposledy přidat objekt, který je <xref:System.ServiceModel.IExtension%601> daného typu.  
  
### <a name="extensible-objects-in-windows-communication-foundation"></a>Rozšiřitelné objekty ve službě Windows Communication Foundation  
 Existují čtyři rozšiřitelné objekty v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]:  
  
-   <xref:System.ServiceModel.ServiceHostBase>– Toto je základní třída pro hostitele služby.  Rozšíření této třídy lze použít k rozšíření chování <xref:System.ServiceModel.ServiceHostBase> sám sebe nebo ukládání stavu pro každou službu.  
  
-   <xref:System.ServiceModel.InstanceContext>– Tato třída připojí instance typu služby s modulem runtime služby.  Obsahuje informace o instanci, jakož i odkaz na <xref:System.ServiceModel.InstanceContext>obsahující <xref:System.ServiceModel.ServiceHostBase>. Rozšíření této třídy lze použít k rozšíření chování <xref:System.ServiceModel.InstanceContext> nebo ukládání stavu pro každou službu.  
  
-   <xref:System.ServiceModel.OperationContext>– Tato třída reprezentuje operaci informace, které shromažďuje modulu runtime pro každou operaci.  To zahrnuje informace, jako je záhlaví příchozích zpráv, příchozí vlastnosti zprávy, příchozí identity zabezpečení a další informace.  Rozšíření této třídy můžete buď rozšířit chování <xref:System.ServiceModel.OperationContext> nebo uložit stav pro každou operaci.  
  
-   <xref:System.ServiceModel.IContextChannel>– Toto rozhraní umožňuje kontrola každý stav pro kanály a proxy servery, které jsou vytvořené [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modulu runtime.  Rozšíření této třídy můžete buď rozšířit chování <xref:System.ServiceModel.IClientChannel> nebo můžete použít k uložení stavu pro každý kanál.  
  
-  
  
 Následující příklad kódu ukazuje použití jednoduchého rozšíření sledovat <xref:System.ServiceModel.InstanceContext> objekty.  
  
 [!code-csharp[IInstanceContextInitializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/iinstancecontextinitializer/cs/initializer.cs#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.IExtensibleObject%601>  
 <xref:System.ServiceModel.IExtension%601>  
 <xref:System.ServiceModel.IExtensionCollection%601>
