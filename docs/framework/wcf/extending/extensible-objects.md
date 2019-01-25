---
title: Rozšiřitelné objekty
ms.date: 03/30/2017
helpviewer_keywords:
- extensible objects [WCF]
ms.assetid: bc88cefc-31fb-428e-9447-6d20a7d452af
ms.openlocfilehash: f2738d6e3a5fc75ab2f5714dc6644267e4fa1e29
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495835"
---
# <a name="extensible-objects"></a>Rozšiřitelné objekty
Vzor rozšiřitelném objektu se používá k buď rozšířit existující třídy modulu runtime s novými funkcemi a přidat nový stav objektu. Rozšíření, připojený k jednomu rozšiřitelné objekty povolit chování na velmi různé fáze zpracování pro přístup k sdílený stav a připojené k běžné rozšiřitelném objektu, který bude mít přístup k funkci.  
  
## <a name="the-iextensibleobjectt-pattern"></a>IExtensibleObject\<T > vzor  
 Existují tři rozhraní ve vzoru rozšiřitelném objektu: <xref:System.ServiceModel.IExtensibleObject%601>, <xref:System.ServiceModel.IExtension%601>, a <xref:System.ServiceModel.IExtensionCollection%601>.  
  
 <xref:System.ServiceModel.IExtensibleObject%601> Rozhraní implementují typy, které umožňují <xref:System.ServiceModel.IExtension%601> objekty přizpůsobit jejich funkce.  
  
 Rozšiřitelné objekty povolit dynamické agregace <xref:System.ServiceModel.IExtension%601> objekty. <xref:System.ServiceModel.IExtension%601> objekty jsou charakteristické následující rozhraní:  
  
```  
public interface IExtension<T>  
where T : IExtensibleObject<T>  
{  
    void Attach(T owner);  
    void Detach(T owner);  
}  
```  
  
 Omezení typu zaručuje, že rozšíření lze definovat pouze pro třídy, které jsou <xref:System.ServiceModel.IExtensibleObject%601>. <xref:System.ServiceModel.IExtension%601.Attach%2A> a <xref:System.ServiceModel.IExtension%601.Detach%2A> poskytují oznámení o agregace nebo členění.  
  
 Je platný pro implementace omezení doby, kdy může být přidávají nebo odebírají z vlastníka. Například můžete zcela zakázat odebrání zákaz přidávání nebo odebírání rozšíření, když vlastník nebo rozšíření a jejich určitého stavu, zakažte přidávajících souběžně více vlastníkům, nebo povolíte jenom jeden záležitostí za nímž následuje jednoho odebrat.  
  
 <xref:System.ServiceModel.IExtension%601> všechny interakce s ostatní standardní spravované rozhraní není určeno. Konkrétně <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> metodu na objekt vlastníka neodpojíte obvykle jeho rozšíření.  
  
 Když rozšíření se přidá do kolekce, <xref:System.ServiceModel.IExtension%601.Attach%2A> je volána před přejde do kolekce. Pokud se rozšíření odebere z kolekce, <xref:System.ServiceModel.IExtension%601.Detach%2A> se volá, když se odebere. To znamená, že (za předpokladu, že příslušné synchronizace) rozšíření můžete spolehnout na pouze nalezen v kolekci, dokud je mezi <xref:System.ServiceModel.IExtension%601.Attach%2A> a <xref:System.ServiceModel.IExtension%601.Detach%2A>.  
  
 Objekt předán <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> nebo <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> nemusí být <xref:System.ServiceModel.IExtension%601> (můžete například předat libovolný objekt), ale vrácené rozšíření je <xref:System.ServiceModel.IExtension%601>.  
  
 Pokud je bez přípony v kolekci <xref:System.ServiceModel.IExtension%601>, <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> , vrátí hodnotu null, a <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> vrátí prázdnou kolekci. Pokud se implementovat několik rozšíření <xref:System.ServiceModel.IExtension%601>, <xref:System.ServiceModel.IExtensionCollection%601.Find%2A> vrátí jeden z nich. Hodnota vrácená z <xref:System.ServiceModel.IExtensionCollection%601.FindAll%2A> je snímek.
  
 Existují dva základní scénáře. První scénář využívá <xref:System.ServiceModel.IExtensibleObject%601.Extensions%2A> vlastnost jako slovník na základě typu vložení stavu objektu chcete povolit jiné součásti a vyhledejte ho pomocí typu.  
  
 Druhý scénář využívá <xref:System.ServiceModel.IExtension%601.Attach%2A> a <xref:System.ServiceModel.IExtension%601.Detach%2A> vlastností objektu se účastnit vlastní chování, jako je registrace k událostem, sledování přechodů mezi stavy a tak dále.  
  
 <xref:System.ServiceModel.IExtensionCollection%601> Rozhraní je kolekce <xref:System.ServiceModel.IExtension%601> objekty, které umožňují načítání <xref:System.ServiceModel.IExtension%601> podle jeho typu. <xref:System.ServiceModel.IExtensionCollection%601.Find%2A?displayProperty=nameWithType> vrací naposledy přidaný objekt, který je <xref:System.ServiceModel.IExtension%601> daného typu.  
  
### <a name="extensible-objects-in-windows-communication-foundation"></a>Rozšiřitelné objekty ve službě Windows Communication Foundation  
 Existují čtyři rozšiřitelné objekty ve Windows Communication Foundation (WCF):  
  
-   <xref:System.ServiceModel.ServiceHostBase> – Toto je základní třídy pro hostitele služby.  Rozšíření této třídy lze použít k rozšíření chování <xref:System.ServiceModel.ServiceHostBase> samotné nebo k ukládání stavu pro každou službu.  
  
-   <xref:System.ServiceModel.InstanceContext> – Tato třída připojuje instance typu služby s modulem runtime služby.  Obsahuje informace o instanci, stejně jako odkaz na <xref:System.ServiceModel.InstanceContext>obsahující <xref:System.ServiceModel.ServiceHostBase>. Rozšíření této třídy lze použít k rozšíření chování <xref:System.ServiceModel.InstanceContext> nebo k ukládání stavu pro každou službu.  
  
-   <xref:System.ServiceModel.OperationContext> – Tato třída reprezentuje informace o operaci, která shromažďuje modul runtime pro každou operaci.  To zahrnuje informace, jako je záhlaví příchozích zpráv, příchozí vlastnosti zprávy, příchozí identity zabezpečení a další informace.  Rozšíření této třídy můžete buď rozšíření chování <xref:System.ServiceModel.OperationContext> nebo uložit stav pro každou operaci.  
  
-   <xref:System.ServiceModel.IContextChannel> – Toto rozhraní umožňuje kontrolu každý stav pro kanály a proxy servery vytvořené modulem WCF runtime.  Rozšíření této třídy můžete buď rozšíření chování <xref:System.ServiceModel.IClientChannel> nebo můžete použít k ukládání stavu pro každý kanál.  
  
-  
  
 Následující příklad kódu ukazuje využití jednoduché rozšíření ke sledování <xref:System.ServiceModel.InstanceContext> objekty.  
  
 [!code-csharp[IInstanceContextInitializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/iinstancecontextinitializer/cs/initializer.cs#1)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.IExtensibleObject%601>
- <xref:System.ServiceModel.IExtension%601>
- <xref:System.ServiceModel.IExtensionCollection%601>
