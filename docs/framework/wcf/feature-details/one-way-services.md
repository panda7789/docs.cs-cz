---
title: Jednosměrné služby
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], one-way service contracts
- WCF [WCF], one-way service contracts
- service contracts [WCF], defining one-way
ms.assetid: 19053a36-4492-45a3-bfe6-0365ee0205a3
ms.openlocfilehash: 011bca07890e706b86f2a0b1dbf11acf77058548
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762485"
---
# <a name="one-way-services"></a>Jednosměrné služby
Výchozí chování operace služby je vzor požadavek odpověď. Ve vzoru požadavek odpověď, klient počká pro zprávy s odpovědí, i v případě, že v kódu, jako je reprezentována operace služby `void` metody. S jednosměrnou operaci se přenášejí pouze jednu zprávu. Příjemce neodešle zprávy s odpovědí, ani nemá odesílatel očekávat jeden.  
  
 Použití jednosměrné návrhový vzor:  
  
- Když klient musí volat operace a nemá vliv výsledek operace na úrovni operace.  
  
- Při použití <xref:System.ServiceModel.NetMsmqBinding> nebo <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> třídy. (Další informace o tomto scénáři najdete v tématu [fronty ve WCF](../../../../docs/framework/wcf/feature-details/queues-in-wcf.md).)  
  
 Když je jednosměrná operace, neexistuje žádná zpráva odpovědi přenášet informace o chybě zpět do klienta. Chybové stavy můžete zjistit pomocí funkce základní vazby, jako je například spolehlivé relace, nebo podle návrhu služby duplexní kontrakt, který používá dvě jednosměrné operace – jednosměrného kontraktu z klienta do služby pro volání operace služby a další Jednosměrná kontraktů mezi klientem a službou tak, aby služba může odesílat back chyb klientovi pomocí zpětného volání, která implementuje klienta.  
  
 Vytvoření kontraktu služby jednosměrné, definování váš kontraktu služby, použije <xref:System.ServiceModel.OperationContractAttribute> třídy pro každou operaci a nastavte <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost `true`, jak je znázorněno v následujícím ukázkovém kódu.  
  
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
  
 Úplný příklad, najdete v článku [jednosměrné](../../../../docs/framework/wcf/samples/one-way.md) vzorku.  
  
## <a name="clients-blocking-with-one-way-operations"></a>Klienti s jednocestné operace blokování  
 Je důležité si uvědomit, zatímco některé jednosměrné aplikace vrací jako odchozí data se zapisují do síťového připojení, v několika situacích implementaci vazby nebo služba může způsobit klienta WCF na blokovat, s využitím jednocestné operace. V klientských aplikací WCF nevrací objekt klienta WCF dokud odchozích dat se zapsala do síťové připojení. To platí pro všechny zprávy exchange vzory, včetně jednocestné operace; To znamená, že jakýkoli problém s psaní že vrácení klienta zabrání data přenosu. V závislosti na problému, může být výsledkem výjimku nebo ke zpoždění při odesílání zpráv do služby.  
  
 Například, pokud přenos nelze najít koncový bod <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType> mnohem neprodleně je vyvolána výjimka. Ale je také možné, že služba nelze číst data vypnutí přenosu z nějakého důvodu, což zabrání přenos klienta odeslat operace vracet. V těchto případech Pokud <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A?displayProperty=nameWithType> období na přenos klienta vazby je překročena, <xref:System.TimeoutException?displayProperty=nameWithType> je vyvolána výjimka – ale ne, dokud se překročil časový limit. Také je možné vyvolat tolik zprávy na službu, službu nemohl zpracovat za určitého bodu. V takovém případě také bloky jednosměrné klienta dokud služba může zpracovat zprávy, nebo dokud je vyvolána výjimka.  
  
 Situace, ve kterém je další variantou službu <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> je nastavena na <xref:System.ServiceModel.ConcurrencyMode.Single> a vazba používá relace. V takovém případě dispečer vynucuje řazení na příchozí zprávy (požadavek relace), který brání dalších zpráv čtená připojen k síti, dokud služba zpracovala předchozí zpráva dané relace. Znovu, bloky klienta, ale Určuje, zda dojde k výjimce závisí na, jestli je služba dokáže zpracovávat data čekání před nastavení časového limitu na straně klienta.  
  
 Některé tento problém můžete zmírnit vložením vyrovnávací paměť mezi objektu klienta a operace odeslání přenos klienta. Například pomocí byla zahájena asynchronní volání nebo pomocí fronty zpráv v paměti služby můžete povolit objektu klienta rychle vrátit. Oba přístupy může zvýšit funkce, ale i nadále vynucovat omezení velikosti fondu vláken a fronty zpráv.  
  
 Doporučujeme, místo toho prozkoumat různé ovládací prvky ve službě i klientovi a poté otestujte vaše aplikace scénáře k určení optimální konfiguraci na obou stranách. Například pokud použití relací blokuje zpracování zpráv pro vaši službu, můžete nastavit <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> vlastnost <xref:System.ServiceModel.InstanceContextMode.PerCall> tak, aby každou zprávu zpracovává instanci a jiné služby a nastavit <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> k <xref:System.ServiceModel.ConcurrencyMode.Multiple> Pokud chcete povolit více než jedno vlákno k odeslání zprávy v čase. Další možností je zvýšit čtení kvóty vazby klienta a služby.  
  
## <a name="see-also"></a>Viz také:

- [Jednosměrný](../../../../docs/framework/wcf/samples/one-way.md)
