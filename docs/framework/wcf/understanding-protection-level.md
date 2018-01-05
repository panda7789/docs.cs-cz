---
title: "Princip úrovně ochrany"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 0c034608-a1ac-4007-8287-b1382eaa8bf2
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c379cf39f30bf7e75907dba5fb06ba4e3862e299
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="understanding-protection-level"></a>Princip úrovně ochrany
`ProtectionLevel` Vlastnost nachází na mnoha různých tříd, jako <xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.OperationContractAttribute> třídy. Vlastnost řídí, jak je chráněný část (nebo celé) zprávy. Toto téma vysvětluje [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] funkce a jak to funguje.  
  
 Pokyny k nastavení úroveň ochrany, najdete v části [postupy: nastavení vlastnosti ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md).  
  
> [!NOTE]
>  Úrovně ochrany lze nastavit pouze v kódu není v konfiguraci.  
  
## <a name="basics"></a>Základy  
 Pochopit funkce úroveň ochrany, platí následující základní příkazy:  
  
-   Existují tři základní úrovně ochrany pro libovolnou část zprávy. Vlastnost (kdekoli se objeví) je nastavena na jednu z <xref:System.Net.Security.ProtectionLevel> hodnot výčtu. Ve vzestupném pořadí ochrany, patří:  
  
    -   `None`.  
  
    -   `Sign`. Chráněné část digitálně podepsané. Tím se zajistí zjišťování manipulaci s částí chráněné zprávy.  
  
    -   `EncryptAndSign`. K zajištění důvěrnosti, než je podepsaný se šifrují část zprávy.  
  
-   Můžete nastavit jenom pro požadavky na ochranu *data aplikací* s touto funkcí. Například WS-Addressing hlavičky jsou data infrastruktury a, proto nemá vliv `ProtectionLevel`.  
  
-   Když je režim zabezpečení nastavená na `Transport`, celé zprávy je chráněný přenosový mechanismus. Nastavení úrovně ochrany samostatné pro různé části zprávu proto nemá žádný vliv.  
  
-   `ProtectionLevel` Je způsob, jak vývojáři nastavit *minimální úroveň stanovenou* které musí dodržovat vazbu. Po nasazení služby se skutečná vazba zadaný v konfiguraci může nebo nemusí podporovat minimální úroveň. Ve výchozím nastavení, například <xref:System.ServiceModel.BasicHttpBinding> třída neposkytuje zabezpečení (i když může být povoleno). Proto pomocí kontrakt, který má jakékoli nastavení jiné než `None` způsobí výjimku, která je vyvolána.  
  
-   Pokud služba vyžaduje, aby minimální `ProtectionLevel` pro všechny zprávy je `Sign`, klient (možná vytvořené jinou hodnotu než[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] technologie) můžete šifrovat a podepsat všechny zprávy (které je větší než požadované minimum). V takovém případě [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] nebude způsobí výjimku, protože klient má provádějí více než požadované minimum. Upozorňujeme však, který [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikace (služby nebo klientů) nebude přepsání zabezpečeného Pokud je to možné část zprávy, ale bude splňovat minimální úroveň. Také Upozorňujeme, že pokud pomocí `Transport` jako režim zabezpečení, přenos může přepsání zabezpečení datového proudu zpráv protože ze své podstaty nelze zabezpečit na podrobnější úrovni.  
  
-   Pokud nastavíte `ProtectionLevel` explicitně buď na kteroukoli `Sign` nebo `EncryptAndSign`, pak musíte použít vazbu s povoleným zabezpečením nebo k výjimce.  
  
-   Pokud vyberete vazbu, která umožňuje zabezpečení a není nastaveno `ProtectionLevel` vlastnost kdekoli v kontrakt, všechny aplikační data budou šifrovaný a podepsaný.  
  
-   Pokud vyberete vazbu, která nemá povoleno zabezpečení (například `BasicHttpBinding` třída má ve výchozím nastavení zakázaná zabezpečení) a `ProtectionLevel` není explicitně nastavena, pak žádná data, aplikace budou chráněné.  
  
-   Pokud používáte vazbu, která se použije zabezpečení na úrovni přenosu, všechna data aplikace nebude zabezpečené podle možnosti přenosu.  
  
-   Pokud používáte vazbu, která se použije zabezpečení na úrovni zpráv, bude podle úrovně ochrany nastavte na kontrakt zabezpečená data aplikací. Pokud nezadáte úroveň ochrany, a všechna data aplikací v zprávy budou šifrovaný a podepsaný.  
  
-   `ProtectionLevel` Lze nastavit na různých úrovních oboru. Existuje hierarchie přidružená k rozsahu, který je vysvětlen v další části.  
  
## <a name="scoping"></a>Obor  
 Nastavení `ProtectionLevel` na volání rozhraní API nejhornější nastaví úroveň pro všechny úrovně pod ním. Pokud `ProtectionLevel` nastavena na jinou hodnotu na nižší úrovni, všechna rozhraní API níže že úrovně v hierarchii bude nyní restartován na novou úroveň (rozhraní API výše, ale stále ovlivní nejvyšší úrovni). V hierarchii je následující. Atributy na stejné úrovni jsou partnerské uzly.  
  
 <xref:System.ServiceModel.ServiceContractAttribute>  
  
 <xref:System.ServiceModel.OperationContractAttribute>  
  
 <xref:System.ServiceModel.FaultContractAttribute>  
  
 <xref:System.ServiceModel.MessageContractAttribute>  
  
 <xref:System.ServiceModel.MessageHeaderAttribute>  
  
 <xref:System.ServiceModel.MessageBodyMemberAttribute>  
  
## <a name="programming-protectionlevel"></a>Programování ProtectionLevel  
 Programu `ProtectionLevel` v libovolném bodě v hierarchii, jednoduše nastavte vlastnost na hodnotu odpovídající při použití atributu. Příklady najdete v tématu [postupy: nastavení vlastnosti ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md).  
  
> [!NOTE]
>  Nastavení vlastnosti na chyb a zpráva kontrakty vyžaduje pochopení, jak tyto funkce fungují. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Postupy: nastavení vlastnosti ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md) a [použití kontraktů zpráv](../../../docs/framework/wcf/feature-details/using-message-contracts.md).  
  
## <a name="ws-addressing-dependency"></a>Adresování WS závislostí  
 Ve většině případů pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ke generování klienta zajišťuje, aby byly identické kontrakty klienta a služby. Však zdánlivě identické kontrakty může způsobit, že klient vyvolá výjimku. K tomu dochází vždy, když vazbu nepodporuje specifikaci WS-Addressing a zadávají se na kontrakt několik úrovní ochrany. Například <xref:System.ServiceModel.BasicHttpBinding> třída nepodporuje specifikace, nebo pokud vytvoříte vlastní vazby, který nepodporuje adresování WS. `ProtectionLevel` Funkce závisí na specifikaci WS-Addressing povolit různých úrovních ochrany na jeden kontrakt. Pokud vazba nepodporuje specifikaci WS-Addressing, všechny úrovně se nastaví na stejnou úroveň ochrany. Úroveň účinnou ochranu pro všechny obory ve smlouvě bude nastavena na nejvyšší úroveň ochrany použít na kontrakt.  
  
 Může dojít k problémům, které je obtížné ladění na první pohled. Je možné vytvořit kontraktu klienta (rozhraní), která obsahuje metody pro více než jedna služba. To znamená stejné rozhraní se používá k vytvoření klienta, který komunikuje s mnoha služeb a rozhraní jeden obsahuje metody pro všechny služby. Vývojář musí postará v tomto scénáři výjimečných volat pouze metody, které platí pro každou konkrétní službu. Pokud je vazba <xref:System.ServiceModel.BasicHttpBinding> třídy, více ochrany úrovně nemůže být podporováno. Odeslání odpovědi klientovi služby však může odpovídat na klienta s nižší úroveň ochrany, než nezbytné. V tomto případě klient vyvolá výjimku, protože se očekává, že vyšší úroveň ochrany.  
  
 Příklad kódu ukazuje tento problém. Následující příklad ukazuje, služby a kontraktu klienta. Předpokládejme, že je vazba [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) element. Všechny operace v kontraktu tedy mít stejnou úroveň ochrany. Tato úroveň ochrany uniform je určen jako úroveň maximální ochrany mezi všechny operace.  
  
 Kontrakt služby je:  
  
 [!code-csharp[c_ProtectionLevel#7](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#7)]
 [!code-vb[c_ProtectionLevel#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#7)]  
  
 Následující kód ukazuje klienta rozhraní kontraktu. Všimněte si, že obsahuje `Tax` metoda, která je určena pro použití s jinou službu:  
  
 [!code-csharp[c_ProtectionLevel#8](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#8)]
 [!code-vb[c_ProtectionLevel#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#8)]  
  
 Když klient zavolá `Price` metody se vyvolá výjimku, pokud neobdrží odpověď ze služby. K tomu dochází, protože klient neurčuje `ProtectionLevel` na `ServiceContractAttribute`, a proto klient používá výchozí (<xref:System.Net.Security.ProtectionLevel.EncryptAndSign>) pro všechny metody, včetně `Price` metoda. Služba ale vrátí se hodnota pomocí <xref:System.Net.Security.ProtectionLevel.Sign> protože kontrakt služby definuje jednu metodu, kterou má úrovně ochrany nastavena na <xref:System.Net.Security.ProtectionLevel.Sign>. V takovém případě bude klient vyvolá chybu, při ověření odpověď ze služby.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 <xref:System.ServiceModel.FaultContractAttribute>  
 <xref:System.ServiceModel.MessageContractAttribute>  
 <xref:System.ServiceModel.MessageHeaderAttribute>  
 <xref:System.ServiceModel.MessageBodyMemberAttribute>  
 <xref:System.Net.Security.ProtectionLevel>  
 [Zabezpečení služeb](../../../docs/framework/wcf/securing-services.md)  
 [Postupy: Nastavení vlastnosti ProtectionLevel](../../../docs/framework/wcf/how-to-set-the-protectionlevel-property.md)  
 [Určování a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)  
 [Použití kontraktů zpráv](../../../docs/framework/wcf/feature-details/using-message-contracts.md)
