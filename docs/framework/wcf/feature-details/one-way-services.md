---
title: Jednosměrné služby
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], one-way service contracts
- WCF [WCF], one-way service contracts
- service contracts [WCF], defining one-way
ms.assetid: 19053a36-4492-45a3-bfe6-0365ee0205a3
ms.openlocfilehash: 0d69af40e4b9a0133e44b64b45466f9aac84ffe2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598746"
---
# <a name="one-way-services"></a>Jednosměrné služby
Výchozím chováním operace služby je vzor požadavek-odpověď. Ve vzoru požadavek-odpověď klient čeká na odpověď, a to i v případě, že je operace služby reprezentována v kódu jako `void` metoda. U jednosměrné operace se přenáší jenom jedna zpráva. Příjemce neposílá zprávu s odpovědí ani odesílatel neočekává.  
  
 Použijte jednosměrný vzor návrhu:  
  
- Když klient musí volat operace a není ovlivněn výsledkem operace na úrovni operace.  
  
- Při použití <xref:System.ServiceModel.NetMsmqBinding> <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> třídy nebo. (Další informace o tomto scénáři najdete v tématu [fronty v WCF](queues-in-wcf.md).)  
  
 Pokud je operace jednosměrná, není k dispozici žádná zpráva s odpovědí, která by mohla přenášet informace o chybách zpět do klienta. Chybové stavy můžete detekovat pomocí funkcí podkladové vazby. například spolehlivé relace nebo návrh duplexního kontraktu služby, který používá 2 1 operací – jednosměrná smlouva od klienta k volání operace služby a další jednosměrnou smlouvu mezi službou a klientem, aby služba mohla odesílat chyby do klienta pomocí zpětného volání, které klient implementuje.  
  
 Chcete-li vytvořit jednosměrný kontrakt služby, definujte kontrakt služby, použijte <xref:System.ServiceModel.OperationContractAttribute> pro každou operaci třídu a nastavte <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost na hodnotu `true` , jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp
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
  
 Úplný příklad naleznete v ukázce [jednosměrového](../samples/one-way.md) vzorku.  
  
## <a name="clients-blocking-with-one-way-operations"></a>Klienti, kteří blokují jednosměrné operace  
 Je důležité si uvědomit, že i když se některé jednosměrné aplikace vrátí hned po zápisu odchozích dat do síťového připojení, v několika scénářích může implementace vazby nebo služby způsobit, že klient WCF bude blokovat pomocí jednosměrných operací. V klientských aplikacích WCF se objekt klienta WCF nevrátí, dokud nebudou výstupní data zapsána do síťového připojení. To platí pro všechny vzory výměny zpráv, včetně jednosměrných operací; To znamená, že při každém problému zápisu dat do přenosu nebude klient vracet. V závislosti na problému může být výsledkem výjimka nebo zpoždění při odesílání zpráv službě.  
  
 Například pokud přenos nemůže najít koncový bod, <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType> je vyvolána výjimka bez nadměrné prodlevy. Je ale také možné, že služba nemůže z nějakého důvodu načíst data z nějakého z důvodů, což zabrání tomu, aby se operace odeslání přenosu od klienta vracela. V takových případech, pokud <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A?displayProperty=nameWithType> je překročena doba pro vazbu přenosů klientů, <xref:System.TimeoutException?displayProperty=nameWithType> je vyvolána výjimka, ale ne až do překročení časového limitu. Je také možné vyvolávat tolik zpráv ve službě, které ji služba nemůže zpracovat po určitou chvíli. V takovém případě je to například jednosměrné klientské bloky, dokud služba nebude moci zpracovat zprávy nebo dokud není vyvolána výjimka.  
  
 Další variantou je situace, kdy <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> je vlastnost služby nastavená na <xref:System.ServiceModel.ConcurrencyMode.Single> a vazba používá relace. V takovém případě dispečer vynutil řazení příchozích zpráv (požadavek relací), což brání v následném čtení těchto zpráv ze sítě, dokud služba nezpracovává předchozí zprávu pro danou relaci. Znovu klientské bloky, ale i to, jestli dojde k výjimce, závisí na tom, jestli je služba schopná zpracovat čekání na data před nastavením časového limitu v klientovi.  
  
 Některé z těchto potíží můžete zmírnit vložením vyrovnávací paměti mezi objektem klienta a operací odeslání klientského přenosu. Například použití asynchronních volání nebo použití fronty zpráv v paměti může umožnit rychlé vrácení objektu klienta. Oba přístupy můžou zvýšit funkčnost, ale velikost fondu vláken a fronty zpráv pořád vynutila omezení.  
  
 Doporučuje se místo toho, abyste prozkoumali různé ovládací prvky ve službě i na straně klienta, a pak otestujete scénáře vaší aplikace a určíte nejlepší konfiguraci na obou stranách. Pokud například použití relací blokuje zpracování zpráv ve službě, můžete nastavit <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> vlastnost na <xref:System.ServiceModel.InstanceContextMode.PerCall> tak, aby každá zpráva mohla být zpracována jinou instancí služby, a nastavit na, aby <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> bylo možné <xref:System.ServiceModel.ConcurrencyMode.Multiple> odesílat zprávy najednou více než jedno vlákno. Další možností je zvýšit kvóty čtení pro vazby služby a klienta.  
  
## <a name="see-also"></a>Viz také

- [Jednosměrný](../samples/one-way.md)
