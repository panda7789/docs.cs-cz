---
title: Jednosměrné služby
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], one-way service contracts
- WCF [WCF], one-way service contracts
- service contracts [WCF], defining one-way
ms.assetid: 19053a36-4492-45a3-bfe6-0365ee0205a3
ms.openlocfilehash: 03efc27f2ba54ca22f03e3ece84770fe0dcadbb3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="one-way-services"></a>Jednosměrné služby
Výchozí chování operace služby je vzor požadavku a odpovědi. V požadavku a odpovědi vzor, klient počká zprávy s odpovědí, i když představuje operaci služby v kódu jako `void` metoda. S Jednosměrná operace se přenášejí pouze jednu zprávu. Příjemce neodesílá zprávu odpovědi, ani nebude odesílatel očekávat jeden.  
  
 Použití vzoru jednosměrný návrhu:  
  
-   Když klient musí volat operace a nemá vliv výsledek operace na úrovni operaci.  
  
-   Při použití <xref:System.ServiceModel.NetMsmqBinding> nebo <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> třídy. (Další informace o tomto scénáři najdete v tématu [fronty ve WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).)  
  
 Když je jednosměrná operace, neexistuje žádná zpráva odpovědi pro přenos informací o chybách zpět do klienta. Chybové stavy můžete zjistit pomocí funkce základní vazby, jako je například spolehlivé relace, nebo podle návrhu duplexní kontrakt služeb, který používá dvě jednosměrná operace – jednosměrného kontraktu z klienta ke službě volat operace služby a jiné jednosměrné smluvním vztahu mezi službou a klienta tak, aby služba můžete odesílat chyb zpět do klienta pomocí zpětné volání, které implementuje klienta.  
  
 K vytvoření kontraktu jednosměrné služby, zadejte své smlouvy, použít <xref:System.ServiceModel.OperationContractAttribute> na každou operaci a nastavit <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost `true`, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOneWayCalculator  
{  
    [OperationContract(IsOneWay=true)]  
    void Add(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Subtract(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Multiply(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Divide(double n1, double n2);  
}  
```  
  
 Úplný příklad, najdete v článku [jednosměrný](../../../../docs/framework/wcf/samples/one-way.md) ukázka.  
  
## <a name="clients-blocking-with-one-way-operations"></a>Klienti blokování pomocí Jednosměrná operace  
 Je důležité si uvědomit, že, zatímco některé jednosměrné aplikace vrací také odchozí data se zapisují do síťového připojení, v několika scénářích implementaci vazby nebo služby může způsobit klienta WCF na blokovat, s využitím Jednosměrná operace. V klientských aplikací WCF objekt klienta WCF nevrací dokud odchozí data byla zapsána na síťové připojení. To platí pro všechny zprávy exchange způsoby, včetně Jednosměrná operace; To znamená, že jakýkoli problém s zápis dat do přenosu vrácení, nemůže klient. V závislosti na problém, může být výsledkem výjimku nebo zpoždění při odesílání zpráv do služby.  
  
 Například, pokud přenos nelze najít koncového bodu <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType> neprodleně mnohem je vyvolána výjimka. Také je však možné, že služba nelze číst data mimo přenosová z nějakého důvodu, což zabraňuje přenos klienta odesilatel operaci vrácení. V těchto případech Pokud <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A?displayProperty=nameWithType> období na přenos klienta vazby překročí, <xref:System.TimeoutException?displayProperty=nameWithType> je vyvolána – ale ne dokud byl překročen časový limit. Je také možné aktivovat mnoho zprávy na službu, službu nemohl zpracovat za určité míry. V takovém případě příliš, jednosměrné klientské bloky dokud služba dokáže zpracovat zprávy, nebo dokud je vyvolána výjimka.  
  
 Další variantou je situace, ve kterém služba <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> je nastavena na <xref:System.ServiceModel.ConcurrencyMode.Single> a vazba používá relací. V takovém případě dispečera vynucuje řazení příchozí zprávy (požadavek relace), která brání následné zprávy při čtení mimo síť, dokud služba zpracovala předchozí zpráva dané relace. Znovu klientské bloky, ale jestli dojde k výjimce závisí na tom, zda služba je schopna zpracovat data čekání před nastavení časový limit na straně klienta.  
  
 Některé tento problém můžete zmírnit tím vložením do vyrovnávací paměti mezi klientského objektu a operaci odeslání přenos klienta. Například pomocí asynchronní volání nebo pomocí frontu v paměti zprávy můžete povolit klientského objektu rychle vrátit. Oba přístupy může zvýšit funkce, ale přesto vynutit omezení velikosti fondu vláken a fronty zpráv.  
  
 Doporučujeme, místo toho zkontrolujte různé ovládací prvky služby, a také na straně klienta a pak scénáře aplikace k určení optimální konfiguraci na obou stranách otestovat. Například pokud použití relací blokuje zpracování zpráv vaší služby, můžete nastavit <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> vlastnost <xref:System.ServiceModel.InstanceContextMode.PerCall> tak, aby každou zprávu zpracovává instanci různé služby a nastavte <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> k <xref:System.ServiceModel.ConcurrencyMode.Multiple> Chcete-li povolit více než jedno vlákno k odesílání zpráv v čase. Další možností je zvýšit čtení kvóty vazeb klienta a služby.  
  
## <a name="see-also"></a>Viz také  
 [Jednosměrný](../../../../docs/framework/wcf/samples/one-way.md)
