---
title: Princip úrovně ochrany
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 0c034608-a1ac-4007-8287-b1382eaa8bf2
ms.openlocfilehash: 90fb844931c3af54367d0e7c14a766636cdcc71a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791427"
---
# <a name="understanding-protection-level"></a>Princip úrovně ochrany
`ProtectionLevel` Vlastnosti se nachází na mnoha různých tříd, jako <xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.OperationContractAttribute> třídy. Vlastnost určuje, jak je chráněné části (nebo celé) zprávy. Toto téma popisuje funkci Windows Communication Foundation (WCF) a jak to funguje.  
  
 Pokyny k nastavení úrovně ochrany, naleznete v tématu [jak: Nastavení vlastnosti ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md).  
  
> [!NOTE]
>  Úrovně ochrany lze nastavit pouze v kódu, není v konfiguraci.  
  
## <a name="basics"></a>Základy  
 Informace o tom funkce úrovně ochrany, platí následující základní příkazy:  
  
- Existují tři základní úrovně ochrany pro žádnou část zprávy. Vlastnost (všude, kde k němu dojde) je nastavena na jednu z <xref:System.Net.Security.ProtectionLevel> hodnot výčtu. Ve vzestupném pořadí ochrany, patří mezi ně:  
  
    - `None`.  
  
    - `Sign`. Chráněná část je digitálně podepsané. Tím se zajistí detekce manipulace s částí chráněné zprávy.  
  
    - `EncryptAndSign`. Část zprávy se šifrují k zajištění důvěrnosti dříve, než je podepsán.  
  
- Můžete nastavit požadavky na ochranu pouze pro *data aplikací* s touto funkcí. Například WS-Addressing záhlaví dat infrastruktury a, proto se nevztahují `ProtectionLevel`.  
  
- Když je režim zabezpečení nastavený na `Transport`, celá zpráva je chráněn přenosový mechanismus. Nastavení úrovně ochrany samostatné pro různé části zprávy, proto nemá žádný vliv.  
  
- `ProtectionLevel` Je způsob, jak vývojáři nastavit *minimální úroveň* , které musí dodržovat vazbu. Při nasazení služby skutečná vazba určená v konfiguraci může nebo nemusí podporovat minimální úroveň. Ve výchozím nastavení, například <xref:System.ServiceModel.BasicHttpBinding> třída neposkytuje zabezpečení (i když může být povoleno). Proto pomocí kontrakt, který má jakékoli nastavení jiné než `None` způsobí vyvolání výjimky.  
  
- Pokud služba vyžaduje, aby minimální `ProtectionLevel` pro všechny zprávy je `Sign`, klienta (například vytvořený technologií jiných WCF) můžete zašifrovat a podepsat všechny zprávy (což je více než požadované minimum). V takovém případě nebude WCF vyvolat výjimku, protože klient má provést více než požadované minimum. Všimněte si však, že nebude over-pass-the secure Pokud je to možné část zprávy aplikací služby WCF (služby nebo klienty), ale bude splňovat minimální úroveň. Všimněte si také, jestli používáte `Transport` jako režim zabezpečení, přenos může over-pass-the secure datového proudu zpráv vzhledem k tomu, že je ze své podstaty nelze zabezpečit na podrobnější úrovni.  
  
- Pokud jste nastavili `ProtectionLevel` explicitně, abyste buď `Sign` nebo `EncryptAndSign`, musíte použít vazbu s povoleným zabezpečením, nebo bude vyvolána výjimka.  
  
- Pokud vyberete vazbu, která umožňuje využívat zabezpečení, a nenastavíte `ProtectionLevel` vlastnost odkudkoli na kontrakt, všechny aplikace, data budou zašifrovaná a podepsaná.  
  
- Pokud vyberete vazbu, která nemá povoleno zabezpečení (třeba `BasicHttpBinding` třída má ve výchozím nastavení zakázané zabezpečení) a `ProtectionLevel` není explicitně nastavena, pak žádná z dat aplikací, budou chráněné.  
  
- Pokud používáte vazbu, která se týká zabezpečení na úrovni přenosu, všechna data aplikací budou zabezpečené podle možnosti přenosu.  
  
- Pokud používáte vazbu, která se týká zabezpečení na úrovni zprávy, se podle úrovně ochrany, nastavte ve smlouvě šifrují data aplikace. Pokud nezadáte úroveň ochrany, všechna data aplikací ve zprávách budou zašifrovaná a podepsaná.  
  
- `ProtectionLevel` Lze nastavit na různých úrovních oboru. Je přidružený k určení oboru, hierarchie, což je vysvětleno v další části.  
  
## <a name="scoping"></a>Vytváření oborů  
 Nastavení `ProtectionLevel` na nejvyšší API nastaví úroveň pro všechny úrovně pod ním. Pokud `ProtectionLevel` je nastavena na jinou hodnotu na nižší úrovni, všechna rozhraní API níže, že úroveň v hierarchii nyní se resetuje na novou úroveň (rozhraní API výše, ale stále ovlivňuje nejvyšší úroveň). Hierarchie je následujícím způsobem. Partnerské uzly jsou atributy na stejné úrovni.  
  
 <xref:System.ServiceModel.ServiceContractAttribute>  
  
 <xref:System.ServiceModel.OperationContractAttribute>  
  
 <xref:System.ServiceModel.FaultContractAttribute>  
  
 <xref:System.ServiceModel.MessageContractAttribute>  
  
 <xref:System.ServiceModel.MessageHeaderAttribute>  
  
 <xref:System.ServiceModel.MessageBodyMemberAttribute>  
  
## <a name="programming-protectionlevel"></a>Programování ProtectionLevel  
 Do programu `ProtectionLevel` kdekoli v hierarchii, stačí nastavit vlastnost na hodnotu odpovídající při použití atributu. Příklady najdete v tématu [jak: Nastavení vlastnosti ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md).  
  
> [!NOTE]
>  Nastavení vlastnosti u chyb a zprávy kontrakty vyžaduje pochopení, jak tyto funkce fungují. Další informace najdete v tématu [jak: Nastavení vlastnosti ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md) a [použití kontraktů zpráv](../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
## <a name="ws-addressing-dependency"></a>WS-Addressing závislostí  
 Ve většině případů použití [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) vygenerovat klienta zajistí, že jsou identické kontrakty klienta a služby. Však zdánlivě identické kontrakty může způsobit, že klient vyvolá výjimku. K tomu dochází vždy, když vazbu nepodporuje specifikaci WS-Addressing a několik úrovní ochrany jsou určeny na kontrakt. Například <xref:System.ServiceModel.BasicHttpBinding> třída nepodporuje specifikaci, nebo pokud vytvoříte vlastní vazby, která nepodporuje WS-Addressing. `ProtectionLevel` Funkce závisí na specifikaci WS-Addressing umožňující různých úrovních ochrany na jeden kontrakt. Pokud se vazba nepodporuje specifikaci WS-Addressing, všechny úrovně se nastaví na stejnou úroveň ochrany. Úroveň účinnou ochranu pro všechny obory ve smlouvě bude nastavena na nejvyšší úroveň ochrany použít u kontraktu.  
  
 To může způsobit problém, který je obtížné ladit na první pohled. Je možné k vytvoření klienta kontraktu (rozhraní), která obsahuje metody pro více než jedna služba. To znamená, že stejné rozhraní se používá k vytvoření klienta, který komunikuje s řadou služeb a jednotné rozhraní obsahuje metody pro všechny služby. Vývojář musí postará v tomto scénáři výjimečných volat pouze metody, které se dají použít u každé konkrétní služby. Je-li vazba <xref:System.ServiceModel.BasicHttpBinding> třídy, více ochrany nelze podporuje úrovně. Odpověď na klienta služby však může odpovídat na klienta s nižší úrovní ochrany než požadované. V tomto případě klient vyvolá výjimku, protože ji očekává, že vyšší úroveň ochrany.  
  
 Příklad kódu ukazuje tento problém. Následující příklad ukazuje, služby a kontrakt klienta. Předpokládejme, že vazba platí [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) elementu. Proto všechny operace v kontraktu a mít stejnou úroveň ochrany. Tato úroveň jednotného ochrany je vyhodnoceno jako úroveň ochrany maximální ve všech operacích.  
  
 Kontrakt služby je:  
  
 [!code-csharp[c_ProtectionLevel#7](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#7)]
 [!code-vb[c_ProtectionLevel#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#7)]  
  
 Následující kód ukazuje klienta rozhraní kontraktu. Všimněte si, že obsahuje `Tax` metodu, která je určena pro použití s jinou službu:  
  
 [!code-csharp[c_ProtectionLevel#8](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#8)]
 [!code-vb[c_ProtectionLevel#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#8)]  
  
 Když klient volá `Price` metody se vyvolá výjimku, když obdrží odpověď ze služby. K tomu dochází, klient neurčuje `ProtectionLevel` na `ServiceContractAttribute`, a proto klient použije výchozí (<xref:System.Net.Security.ProtectionLevel.EncryptAndSign>) pro všechny metody, včetně `Price` – metoda. Ale služba vrátí hodnotu používanou <xref:System.Net.Security.ProtectionLevel.Sign> protože kontrakt služby definuje jedinou metodu, která se má nastavit na úrovni ochrany <xref:System.Net.Security.ProtectionLevel.Sign>. V tomto případě klient vyvolá chybu při ověřování odpověď ze služby.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageHeaderAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- <xref:System.Net.Security.ProtectionLevel>
- [Zabezpečení služeb](../../../docs/framework/wcf/securing-services.md)
- [Postupy: Nastavení vlastnosti ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)
- [Určování a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
- [Použití kontraktů zpráv](../../../docs/framework/wcf/feature-details/using-message-contracts.md)
