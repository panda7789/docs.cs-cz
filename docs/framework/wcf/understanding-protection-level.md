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
ms.openlocfilehash: 896b75d3dfb5ebace9bef0c410e4a86dfb765bd8
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321519"
---
# <a name="understanding-protection-level"></a>Princip úrovně ochrany

Vlastnost `ProtectionLevel` se nachází na mnoha různých třídách, jako jsou <xref:System.ServiceModel.ServiceContractAttribute> a třídy <xref:System.ServiceModel.OperationContractAttribute>. Vlastnost určuje, jak je část (neboli celá) zprávy chráněná. Toto téma vysvětluje funkci Windows Communication Foundation (WCF) a jak funguje.

Pokyny k nastavení úrovně ochrany najdete v tématu [Postupy: nastavení vlastnosti ProtectionLevel](how-to-set-the-protectionlevel-property.md).

> [!NOTE]
> Úrovně ochrany lze nastavit pouze v kódu, nikoli v konfiguraci.

## <a name="basics"></a>Základy

Pro pochopení funkce úrovně ochrany platí následující základní příkazy:

- Pro jakoukoli část zprávy existují tři základní úrovně ochrany. Vlastnost (kdekoli k ní) je nastavena na jednu z hodnot <xref:System.Net.Security.ProtectionLevel> výčtu. Ve vzestupném pořadí ochrany zahrnují:

  - `None`.

  - `Sign`. Chráněná součást je digitálně podepsaná. Tím se zajistí detekce jakékoli manipulace s částkou chráněné zprávy.

  - `EncryptAndSign`. Část zprávy je zašifrovaná, aby před podepsáním zajistila důvěrnost.

- Požadavky na ochranu můžete nastavit jenom pro *data aplikace* pomocí této funkce. Například hlavičky WS-Addressing jsou data infrastruktury, a proto nejsou ovlivněny `ProtectionLevel`.

- Když je režim zabezpečení nastavený na `Transport`, celá zpráva je chráněná transportním mechanismem. Proto nastavení samostatné úrovně ochrany pro různé části zprávy nemá žádný vliv.

- `ProtectionLevel` je způsob, jak vývojářům nastavit *minimální úroveň* , kterou musí vazba splňovat. Když je služba nasazená, skutečná vazba zadaná v konfiguraci může nebo nemusí podporovat minimální úroveň. Například ve výchozím nastavení třída <xref:System.ServiceModel.BasicHttpBinding> neposkytuje zabezpečení (i když je možné ji povolit). Proto použití s kontraktem, který má jakékoliv nastavení jiné než `None` způsobí vyvolání výjimky.

- Pokud služba vyžaduje, aby byl `Sign``ProtectionLevel` pro všechny zprávy, klient (možná vytvořený pomocí technologie jiného typu než WCF) může šifrovat a podepisovat všechny zprávy (což je více než minimální požadovaná). V tomto případě WCF nevyvolá výjimku, protože klient má více než minimum. Upozorňujeme však, že aplikace WCF (služby nebo klienti) nezabezpečují část zprávy, pokud je to možné, ale budou odpovídat minimální úrovni. Všimněte si také, že při použití `Transport` jako režimu zabezpečení může přenos přenášet datový proud zpráv, protože je ze své podstaty neschopen zabezpečit na podrobnější úrovni.

- Nastavíte-li `ProtectionLevel` explicitně buď na `Sign` nebo `EncryptAndSign`, je nutné použít vazbu s povoleným zabezpečením nebo bude vyvolána výjimka.

- Pokud vyberete vazbu, která umožňuje zabezpečení, a nenastavíte vlastnost `ProtectionLevel` kdekoli u smlouvy, všechna data aplikace budou šifrovaná a podepsaná.

- Pokud vyberete vazbu, u které není povolené zabezpečení (například třída `BasicHttpBinding` má ve výchozím nastavení zakázané zabezpečení) a `ProtectionLevel` není explicitně nastavená, žádná data aplikace nebudou chráněná.

- Pokud používáte vazbu, která používá zabezpečení na úrovni přenosu, všechna data aplikace budou zabezpečena podle schopností přenosu.

- Použijete-li vazbu, která aplikuje zabezpečení na úrovni zprávy, budou data aplikace zabezpečena podle úrovní ochrany stanovených ve smlouvě. Pokud nezadáte úroveň ochrany, všechna data aplikace ve zprávách budou šifrována a podepsána.

- `ProtectionLevel` lze nastavit na různých úrovních oboru. K oboru je přidružena hierarchie, která je vysvětlena v následující části.

## <a name="scoping"></a>Rozsah

Nastavení `ProtectionLevel` na nejvyšší úrovni rozhraní API nastaví úroveň pro všechny úrovně pod ní. Pokud je `ProtectionLevel` nastavená na jinou hodnotu na nižší úrovni, všechna rozhraní API pod touto úrovní v hierarchii se teď obnoví na novou úroveň (rozhraní API nad ní se ale budou dál týkat nejvyšší úrovně). Hierarchie je následující. Atributy na stejné úrovni jsou partnerské uzly.

- <xref:System.ServiceModel.ServiceContractAttribute>

- <xref:System.ServiceModel.OperationContractAttribute>

- <xref:System.ServiceModel.FaultContractAttribute>

- <xref:System.ServiceModel.MessageContractAttribute>

- <xref:System.ServiceModel.MessageHeaderAttribute>

- <xref:System.ServiceModel.MessageBodyMemberAttribute>

## <a name="programming-protectionlevel"></a>Programování ProtectionLevel

Chcete-li programovat `ProtectionLevel` v jakémkoli bodě hierarchie, jednoduše nastavte vlastnost na odpovídající hodnotu při použití atributu. Příklady naleznete v tématu [How to: set a vlastnost ProtectionLevel](how-to-set-the-protectionlevel-property.md).

> [!NOTE]
> Nastavení vlastnosti u chyb a kontraktů zpráv vyžaduje porozumění fungování těchto funkcí. Další informace najdete v tématu [Postupy: nastavení vlastnosti ProtectionLevel](how-to-set-the-protectionlevel-property.md) a [používání kontraktů zpráv](./feature-details/using-message-contracts.md).

## <a name="ws-addressing-dependency"></a>Závislost WS-Addressing

Ve většině případů použití nástroje pro vytváření [metadat (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) pro vygenerování klienta zajistí, že kontrakty klientů a služeb jsou identické. Zdánlivě identické kontrakty ale mohou způsobit výjimku klienta. K tomu dochází vždy, když vazba nepodporuje specifikaci WS-Addressing a v kontraktu je zadáno několik úrovní ochrany. Například třída <xref:System.ServiceModel.BasicHttpBinding> nepodporuje specifikaci, nebo pokud vytvoříte vlastní vazbu, která nepodporuje WS-Addressing. Funkce `ProtectionLevel` spoléhá na specifikaci WS-Addressing, která pro jednu smlouvu povoluje různé úrovně ochrany. Pokud vazba nepodporuje specifikaci WS-Addressing, všechny úrovně se nastaví na stejnou úroveň ochrany. Účinná úroveň ochrany pro všechny obory ve smlouvě bude nastavena na nejsilnější úroveň ochrany použitou ve smlouvě.

To může způsobit problém, který je obtížné ladit na první pohled. Je možné vytvořit kontrakt klienta (rozhraní), který obsahuje metody pro více než jednu službu. To znamená, že se stejné rozhraní používá k vytvoření klienta, který komunikuje s mnoha službami, a jediné rozhraní obsahuje metody pro všechny služby. Vývojář se musí v tomto vzácném scénáři zajímat, aby vyvolal pouze ty metody, které platí pro konkrétní službu. Pokud je vazba třídu <xref:System.ServiceModel.BasicHttpBinding>, nelze podporovat více úrovní ochrany. Nicméně odpověď na službu klienta může reagovat na klienta s nižší úrovní ochrany, než je nutné. V takovém případě bude klient generovat výjimku, protože očekává vyšší úroveň ochrany.

Příklad kódu tento problém ilustruje. Následující příklad ukazuje službu a kontrakt klienta. Předpokládejme, že vazba je [\<basicHttpBinding >](../configure-apps/file-schema/wcf/basichttpbinding.md) elementu. Proto všechny operace na kontraktu mají stejnou úroveň ochrany. Tato jednotná úroveň ochrany je určena jako maximální úroveň ochrany napříč všemi operacemi.

Kontrakt služby je:

[!code-csharp[c_ProtectionLevel#7](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#7)]
[!code-vb[c_ProtectionLevel#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#7)]

Následující kód ukazuje rozhraní kontraktu klienta. Všimněte si, že obsahuje `Tax` metodu, která je určena pro použití s jinou službou:

[!code-csharp[c_ProtectionLevel#8](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#8)]
[!code-vb[c_ProtectionLevel#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#8)]

Když klient zavolá metodu `Price`, vyvolá výjimku, když obdrží odpověď od služby. K tomu dochází, protože klient neurčuje `ProtectionLevel` na `ServiceContractAttribute`a klient proto používá výchozí (<xref:System.Net.Security.ProtectionLevel.EncryptAndSign>) pro všechny metody, včetně metody `Price`. Služba však vrací hodnotu pomocí <xref:System.Net.Security.ProtectionLevel.Sign> úrovně, protože kontrakt služby definuje jedinou metodu, která má úroveň ochrany nastavenou na hodnotu <xref:System.Net.Security.ProtectionLevel.Sign>. V takovém případě klient při ověřování odpovědi ze služby vyvolá chybu.

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageHeaderAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- <xref:System.Net.Security.ProtectionLevel>
- [Zabezpečení služeb](securing-services.md)
- [Postupy: Nastavení vlastnosti ProtectionLevel](how-to-set-the-protectionlevel-property.md)
- [Určování a zpracování chyb v kontraktech a službách](specifying-and-handling-faults-in-contracts-and-services.md)
- [Použití kontraktů zpráv](./feature-details/using-message-contracts.md)
