---
title: Navrhování kontraktů služby
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF]
ms.assetid: 8e89cbb9-ac84-4f0d-85ef-0eb6be0022fd
ms.openlocfilehash: 37723011d69e8ea2ead3f7a30a30898dede054cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176679"
---
# <a name="designing-service-contracts"></a>Navrhování kontraktů služby
Toto téma popisuje, jaké jsou servisní smlouvy, jak jsou definovány, jaké operace jsou k dispozici (a důsledky pro podkladové výměny zpráv), jaké datové typy se používají a další problémy, které vám pomohou navrhnout operace, které splňují požadavky vašeho scénáře.  
  
## <a name="creating-a-service-contract"></a>Vytvoření servisní smlouvy  
 Služby vystavit řadu operací. V aplikacích Windows Communication Foundation (WCF) definujte operace vytvořením metody a jejím označením atributem. <xref:System.ServiceModel.OperationContractAttribute> Potom vytvořit servisní smlouvu, seskupit své operace, buď deklarováním je v rámci rozhraní označené atributem <xref:System.ServiceModel.ServiceContractAttribute> nebo jejich definováním ve třídě označené stejným atributem. (Základní příklad naleznete v [tématu How to: Define a Service Contract](how-to-define-a-wcf-service-contract.md).)  
  
 Všechny metody, které <xref:System.ServiceModel.OperationContractAttribute> nemají atribut nejsou operace služby a nejsou vystaveny wcf služby.  
  
 Toto téma popisuje následující body rozhodnutí při navrhování servisní smlouvy:  
  
- Určuje, zda se mají používat třídy nebo rozhraní.  
  
- Jak určit datové typy, které chcete vyměňovat.  
  
- Typy vzorů výměny, které můžete použít.  
  
- Zda můžete explicitní požadavky na zabezpečení součástí smlouvy.  
  
- Omezení pro provozní vstupy a výstupy.  
  
## <a name="classes-or-interfaces"></a>Třídy nebo rozhraní  
 Třídy a rozhraní představují seskupení funkcí a proto oba lze definovat wcf smlouvy o poskytování služeb. Doporučujeme však používat rozhraní, protože přímo modelují smlouvy o poskytování služeb. Bez implementace rozhraní nevíce než definovat seskupení metod s určitými podpisy. Implementujte rozhraní smlouvy o poskytování služeb a implementovali jste službu WCF.  
  
 Všechny výhody spravovaných rozhraní se vztahují na rozhraní servisní smlouvy:  
  
- Rozhraní servisní smlouvy můžete rozšířit libovolný počet dalších rozhraní servisní smlouvy.  
  
- Jedna třída může implementovat libovolný počet smluv o poskytování služeb implementací těchto rozhraní servisní smlouvy.  
  
- Implementaci smlouvy o poskytování služeb můžete upravit změnou implementace rozhraní, zatímco servisní smlouva zůstává stejná.  
  
- Můžete verzi služby implementací staré rozhraní a nové. Staří klienti se připojují k původní verzi, zatímco novější klienti se mohou připojit k novější verzi.  
  
> [!NOTE]
> Při dědění z jiných rozhraní servisní smlouvy nelze přepsat vlastnosti operace, jako je například název nebo obor názvů. Pokud se o to pokusíte, vytvoříte novou operaci v aktuální servisní smlouvě.  
  
 Příklad použití rozhraní k vytvoření smlouvy o poskytování služeb naleznete v tématu [How to: Create a Service with a Contract Interface](./feature-details/how-to-create-a-service-with-a-contract-interface.md).  
  
 Třídu však můžete použít k definování smlouvy o poskytování služeb a k implementaci této smlouvy současně. Výhodou vytváření služeb použitím <xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.OperationContractAttribute> přímo do třídy a metody na třídu, respektive je rychlost a jednoduchost. Nevýhodou je, že spravované třídy nepodporují vícenásobné dědičnosti a v důsledku toho mohou implementovat pouze jednu smlouvu o poskytování služeb najednou. Kromě toho všechny změny podpisů třídy nebo metody upraví veřejnou smlouvu pro tuto službu, což může zabránit nezměněných klientů v používání služby. Další informace naleznete [v tématu Implementace servisních smluv](implementing-service-contracts.md).  
  
 Příklad, který používá třídu k vytvoření smlouvy o poskytování služeb a implementuje ji současně, naleznete v [tématu How to: Create a Service with a Contract Class](./feature-details/how-to-create-a-wcf-contract-with-a-class.md).  
  
 V tomto okamžiku byste měli pochopit rozdíl mezi definováním smlouvy o poskytování služeb pomocí rozhraní a pomocí třídy. Dalším krokem je rozhodnutí, jaká data mohou být předávána tam a zpět mezi službou a jejími klienty.  
  
## <a name="parameters-and-return-values"></a>Parametry a návratové hodnoty  
 Každá operace má vrácenou hodnotu a `void`parametr, i když se jedná o . Však na rozdíl od místní metody, ve kterém můžete předat odkazy na objekty z jednoho objektu do druhého, operace služby nepředávají odkazy na objekty. Místo toho předávají kopie objektů.  
  
 To je významné, protože každý typ použitý v parametru nebo vrácené hodnotě musí být serializovatelný; to znamená, že musí být možné převést objekt tohoto typu na proud bajtů a z proudu bajtů na objekt.  
  
 Primitivní typy jsou serializovatelné ve výchozím nastavení, stejně jako mnoho typů v rozhraní .NET Framework.  
  
> [!NOTE]
> Hodnota názvů parametrů v podpisu operace je součástí smlouvy a rozlišují malá a velká písmena. Pokud chcete použít stejný název parametru místně, ale změnit název v <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>publikovaných metadatech, naleznete v .  
  
#### <a name="data-contracts"></a>Kontrakty dat  
 Aplikace orientované na služby, jako jsou aplikace Windows Communication Foundation (WCF), jsou navrženy tak, aby spolupracovaly s co nejširším počtem klientských aplikací na platformách Microsoft i jiných společností. Pro co nejširší možnou interoperabilitu se <xref:System.Runtime.Serialization.DataContractAttribute> doporučuje <xref:System.Runtime.Serialization.DataMemberAttribute> označit typy atributy a vytvořit kontrakt dat, což je část smlouvy o poskytování služeb, která popisuje data, která si vyměňují operace služby.  
  
 Kontrakty dat jsou smlouvy stylu opt-in: Žádný typ nebo datový člen není serializován, pokud explicitně nepoužijete atribut kontraktu dat. Kontrakty dat nesouvisejí s rozsahem přístupu spravovaného kódu: Soukromé datové členy lze serializovat a odeslat jinam, aby k nim bylo veřejně přístupné. (Základní příklad kontraktu dat naleznete v tématu [How to: Create a Basic Data Contract for a Class or Structure](./feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md).) WCF zpracovává definici podkladové zprávy SOAP, které umožňují funkce operace, jakož i serializace datových typů do a z těla zpráv. Dokud jsou vaše datové typy serializovatelné, není nutné přemýšlet o základní infrastruktury výměny zpráv při navrhování operací.  
  
 Přestože typická aplikace <xref:System.Runtime.Serialization.DataContractAttribute> WCF používá atributy a <xref:System.Runtime.Serialization.DataMemberAttribute> k vytvoření datových kontraktů pro operace, můžete použít jiné mechanismy serializace. Standard <xref:System.Runtime.Serialization.ISerializable> <xref:System.SerializableAttribute> a <xref:System.Xml.Serialization.IXmlSerializable> mechanismy všechny práce pro zpracování serializace datových typů do podkladové zprávy SOAP, které přenášejí z jedné aplikace do druhé. Pokud vaše datové typy vyžadují zvláštní podporu, můžete použít další strategie serializace. Další informace o možnostech serializace datových typů v aplikacích WCF naleznete v [tématu Určení přenosu dat ve smlouvách o poskytování služeb](./feature-details/specifying-data-transfer-in-service-contracts.md).  
  
#### <a name="mapping-parameters-and-return-values-to-message-exchanges"></a>Mapování parametrů a návratových hodnot do výměny zpráv  
 Operace služby jsou podporovány základní výměnou zpráv SOAP, které přenášejí data aplikace tam a zpět, kromě dat požadovaných aplikací pro podporu určitých standardních funkcí zabezpečení, transakcí a relace. Vzhledem k tomu, že se jedná o tento případ, podpis operace služby určuje určitý vzor *výměny zpráv* (MEP), který může podporovat přenos dat a funkce, které operace vyžaduje. V programovacím modelu WCF můžete zadat tři vzory: vzorové zprávy požadavek/odpověď, jednosměrné a duplexní zprávy.  
  
##### <a name="requestreply"></a>Požadavek/odpověď  
 Vzor požadavku/odpovědi je ten, ve kterém odesílatel požadavku (klientská aplikace) obdrží odpověď, se kterou je požadavek korelován. Toto je výchozí MEP, protože podporuje operaci, ve kterém jeden nebo více parametrů jsou předány do operace a vrácená hodnota je předána zpět volajícímu. Například následující příklad kódu Jazyka C# ukazuje základní operaci služby, která přebírá jeden řetězec a vrací řetězec.  
  
```csharp  
[OperationContractAttribute]  
string Hello(string greeting);  
```  
  
 Následuje ekvivalentní kód jazyka Visual Basic.  
  
```vb  
<OperationContractAttribute()>  
Function Hello (ByVal greeting As String) As String  
```  
  
 Tento podpis operace určuje formu podkladové výměny zpráv. Pokud neexistuje žádná korelace, WCF nelze určit, pro kterou operaci je vrácená hodnota určena.  
  
 Všimněte si, že pokud zadáte jiný vzor `void` základní`Nothing` zprávy, i operace služby, které vracejí (v jazyce Visual Basic) jsou výměny zpráv požadavku a odpovědi. Výsledkem pro vaši operaci je, že pokud klient vyvolá operaci asynchronně, klient zastaví zpracování, dokud je přijata vrácená zpráva, i když tato zpráva je prázdná v normálním případě. Následující příklad kódu jazyka C# ukazuje operaci, která se nevrátí, dokud klient obdržel prázdnou zprávu v odpovědi.  
  
```csharp  
[OperationContractAttribute]  
void Hello(string greeting);  
```  
  
 Následuje ekvivalentní kód jazyka Visual Basic.  
  
```vb  
<OperationContractAttribute()>  
Sub Hello (ByVal greeting As String)  
```  
  
 Předchozí příklad může zpomalit výkon klienta a odezvu, pokud operace trvá dlouhou dobu, ale existují `void`výhody pro operace požadavku/odpovědi i v případě, že vrátí . Nejzřejmější je, že chyby SOAP mohou být vráceny ve zprávě odpovědi, což znamená, že došlo k chybě související se službou, ať už v komunikaci nebo zpracování. Chyby SOAP, které jsou zadány v servisní smlouvě, jsou předány klientské aplikaci jako <xref:System.ServiceModel.FaultException%601> objekt, kde parametr typu je typ zadaný v servisní smlouvě. To usnadňuje upozorňování klientů na chybové stavy ve službách WCF. Další informace o výjimkách, chybách SOAP a zpracování chyb naleznete [v tématu Určení a zpracování chyb ve smlouvách a službách](specifying-and-handling-faults-in-contracts-and-services.md). Příklad služby požadavku/odpovědi a klienta naleznete v [tématu How to: Create a Request-Reply Contract](./feature-details/how-to-create-a-request-reply-contract.md). Další informace o problémech se vzorem požadavku a odpovědi naleznete v tématu [Request-Reply Services](./feature-details/request-reply-services.md).  
  
##### <a name="one-way"></a>Jednosměrné  
 Pokud klient aplikace služby WCF by neměl čekat na dokončení operace a nezpracovává chyby SOAP, operace může určit vzor jednosměrné zprávy. Jednosměrná operace je operace, ve kterém klient vyvolá operaci a pokračuje ve zpracování po WCF zapíše zprávu do sítě. Obvykle to znamená, že pokud data odesílaná v odchozí zprávě je velmi velký klient pokračuje v běhu téměř okamžitě (pokud není chyba odesílání dat). Tento typ vzoru výměny zpráv podporuje chování podobné událostem z klienta do aplikace služby.  
  
 Výměna zpráv, ve které je odeslána jedna zpráva a žádná není přijata, nemůže podporovat operaci služby, která určuje jinou vrácenou hodnotu než `void`; v tomto <xref:System.InvalidOperationException> případě je vyvolána výjimka.  
  
 Žádná vrácená zpráva také znamená, že nemůže být vrácena žádná chyba SOAP, která označuje chyby při zpracování nebo komunikaci. (Komunikace informací o chybách při operacích jsou jednosměrné operace vyžaduje duplexní text výměny zpráv.)  
  
 Chcete-li zadat jednosměrnou výměnu zpráv `void`pro operaci, která vrátí , nastavte <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost na `true`, jako v následujícím příkladu kódu Jazyka C#.  
  
```csharp  
[OperationContractAttribute(IsOneWay=true)]  
void Hello(string greeting);  
```  
  
 Následuje ekvivalentní kód jazyka Visual Basic.  
  
```vb  
<OperationContractAttribute(IsOneWay := True)>  
Sub Hello (ByVal greeting As String)  
```  
  
 Tato metoda je shodná s předchozím příkladem požadavku/odpovědi, ale nastavení <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnosti na `true` znamená, že i když je metoda identická, operace služby neodešle návratovou zprávu a klienti se okamžitě vrátí, jakmile byla odchozí zpráva předána vrstvě kanálu. Příklad najdete v [tématu How to: Create a One-Way Contract](./feature-details/how-to-create-a-one-way-contract.md). Další informace o jednosměrném vzoru naleznete v [tématu Jednosměrné služby](./feature-details/one-way-services.md).  
  
##### <a name="duplex"></a>Duplex  
 Duplexní vzor je charakterizován schopností služby i klienta odesílat zprávy navzájem nezávisle, zda používáte jednosměrné zasílání zpráv nebo zasílání zpráv požadavku/odpovědi. Tato forma obousměrné komunikace je užitečná pro služby, které musí komunikovat přímo klientovi nebo pro poskytování asynchronní hozachy na obou stranách výměny zpráv, včetně chování podobné události.  
  
 Duplexní vzor je o něco složitější než požadavek/odpověď nebo jednosměrné vzory z důvodu další mechanismus pro komunikaci s klientem.  
  
 Chcete-li navrhnout duplexní smlouvu, musíte také navrhnout smlouvu zpětného volání a přiřadit typ této smlouvy zpětného volání <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> vlastnosti atributu, <xref:System.ServiceModel.ServiceContractAttribute> který označuje smlouvu o poskytování služeb.  
  
 Chcete-li implementovat duplexní vzor, musíte vytvořit druhé rozhraní, které obsahuje deklarace metody, které jsou volány na straně klienta.  
  
 Příklad vytvoření služby a klienta, který k této službě přistupuje, najdete v tématu [Postup: Vytvoření duplexní smlouvy](./feature-details/how-to-create-a-duplex-contract.md) a [Postup: Přístup ke službám s duplexní smlouvou](./feature-details/how-to-access-services-with-a-duplex-contract.md). Pracovní ukázku naleznete v tématu [Duplex](./samples/duplex.md). Další informace o problémech s duplexními smlouvami naleznete v [tématu Duplex Services](./feature-details/duplex-services.md).  
  
> [!CAUTION]
> Když služba obdrží duplexní zprávu, vyhledá `ReplyTo` prvek v této příchozí zprávy k určení, kam odeslat odpověď. Pokud kanál, který se používá k přijetí zprávy není zabezpečena, pak nedůvěryhodný klient `ReplyTo`může odeslat škodlivou zprávu s cílový počítač , což vede k odmítnutí služby (DOS) tohoto cílového počítače.  
  
##### <a name="out-and-ref-parameters"></a>Out a Ref Parametry  
 Ve většině případů můžete `in` použít`ByVal` parametry ( `out` v `ref` jazyce`ByRef` Visual Basic) a parametry ( v jazyce Visual Basic). Vzhledem `out` `ref` k tomu, že oba parametry označují, že data jsou vrácena z operace, podpis operace, `void`jako je například následující, určuje, že je vyžadována operace požadavku a odpovědi, i když se vrátí podpis operace .  
  
```csharp  
[ServiceContractAttribute]  
public interface IMyContract  
{  
  [OperationContractAttribute]  
  public void PopulateData(ref CustomDataType data);  
}  
```  
  
 Následuje ekvivalentní kód jazyka Visual Basic.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface IMyContract  
  <OperationContractAttribute()> _  
  Public Sub PopulateData(ByRef data As CustomDataType)  
End Interface  
```  
  
 Jedinou výjimkou jsou případy, ve kterých má váš podpis určitou strukturu. Vazbu <xref:System.ServiceModel.NetMsmqBinding> můžete například použít ke komunikaci s klienty pouze v `void`případě, že metoda použitá k deklarování operace vrátí ; nemůže existovat žádná výstupní hodnota, zda se `ref`jedná `out` o vrácenou hodnotu nebo parametr.  
  
 Kromě toho `out` použití `ref` nebo parametry vyžaduje, aby operace mít základní zprávu odpovědi k přenosu zpět změněný objekt. Pokud je operace jednosměrná operace, <xref:System.InvalidOperationException> je vyvolána výjimka za běhu.  
  
### <a name="specify-message-protection-level-on-the-contract"></a>Zadat úroveň ochrany zpráv ve smlouvě  
 Při navrhování smlouvy, musíte také rozhodnout úroveň ochrany zpráv služeb, které implementují smlouvu. To je nezbytné pouze v případě, že zabezpečení zprávy se použije na vazbu v koncovém bodě smlouvy. Pokud vazba má zabezpečení vypnuto (to znamená, pokud <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> systémová <xref:System.ServiceModel.SecurityMode.None?displayProperty=nameWithType>vazba nastaví na hodnotu ), pak není třeba rozhodnout o úroveň ochrany zpráv pro smlouvu. Ve většině případů systémem poskytované vazby s zabezpečením na úrovni zprávy poskytují dostatečnou úroveň ochrany a není třeba vzít v úvahu úroveň ochrany pro každou operaci nebo pro každou zprávu.  
  
 Úroveň ochrany je hodnota, která určuje, zda jsou zprávy (nebo části zpráv), které podporují službu, podepsány, podepsány a šifrovány nebo odeslány bez podpisů nebo šifrování. Úroveň ochrany lze nastavit v různých oborech: Na úrovni služby, pro konkrétní operaci, pro zprávu v rámci této operace nebo část zprávy. Hodnoty nastavené v jednom oboru se stanou výchozí hodnotou pro menší obory, pokud nejsou explicitně přepsány. Pokud konfigurace vazby nemůže poskytnout požadovanou minimální úroveň ochrany pro smlouvu, je vyvolána výjimka. A pokud žádné hodnoty úrovně ochrany jsou explicitně nastaveny na smlouvy, konfigurace vazby řídí úroveň ochrany pro všechny zprávy, pokud vazba má zabezpečení zprávy. Toto je výchozí chování.  
  
> [!IMPORTANT]
> Rozhodování o tom, zda explicitně nastavit různé rozsahy smlouvy <xref:System.Net.Security.ProtectionLevel.EncryptAndSign?displayProperty=nameWithType> na méně než plnou úroveň ochrany je obecně rozhodnutí, které obchoduje určitý stupeň zabezpečení pro zvýšení výkonu. V těchto případech se vaše rozhodnutí musí točit kolem vašich operací a hodnoty dat, které si vyměňují. Další informace naleznete [v tématu Zabezpečení služeb](securing-services.md).  
  
 Například následující příklad kódu nenastaví <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> vlastnost <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> i vlastnost ve smlouvě.  
  
```csharp  
[ServiceContract]  
public interface ISampleService  
{  
  [OperationContractAttribute]  
  public string GetString();  
  
  [OperationContractAttribute]  
  public int GetInt();
}  
```  
  
 Následuje ekvivalentní kód jazyka Visual Basic.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface ISampleService  
  
  <OperationContractAttribute()> _  
  Public Function GetString()As String  
  
  <OperationContractAttribute()> _  
  Public Function GetData() As Integer  
  
End Interface  
```  
  
 Při interakci s `ISampleService` implementací v koncovém bodu <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>s <xref:System.ServiceModel.SecurityMode.Message>výchozím <xref:System.ServiceModel.WSHttpBinding> (výchozí , což je ) jsou všechny zprávy šifrovány a podepsány, protože se jedná o výchozí úroveň ochrany. Však při `ISampleService` použití služby <xref:System.ServiceModel.BasicHttpBinding> s výchozí <xref:System.ServiceModel.SecurityMode>(výchozí <xref:System.ServiceModel.SecurityMode.None>, což je ), všechny zprávy jsou odesílány jako text, protože neexistuje žádné zabezpečení pro tuto vazbu a tak úroveň ochrany je ignorována (to znamená, že zprávy nejsou šifrovány ani podepsány). Pokud <xref:System.ServiceModel.SecurityMode> byla změněna na <xref:System.ServiceModel.SecurityMode.Message>, pak tyto zprávy by být šifrovány a podepsány (protože to by nyní výchozí úroveň ochrany vazby).  
  
 Pokud chcete explicitně zadat nebo upravit požadavky na <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> ochranu smlouvy, `ProtectionLevel` nastavte vlastnost (nebo některou z vlastností v menším oboru) na úroveň, kterou vyžaduje servisní smlouva. V tomto případě použití explicitní nastavení vyžaduje vazbu na podporu, že nastavení na minimum pro použitý obor. Například následující příklad kódu určuje <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> jednu hodnotu explicitně pro `GetGuid` operaci.  
  
```csharp  
[ServiceContract]  
public interface IExplicitProtectionLevelSampleService  
{  
  [OperationContractAttribute]  
  public string GetString();  
  
  [OperationContractAttribute(ProtectionLevel=ProtectionLevel.None)]  
  public int GetInt();
  [OperationContractAttribute(ProtectionLevel=ProtectionLevel.EncryptAndSign)]  
  public int GetGuid();
}  
```  
  
 Následuje ekvivalentní kód jazyka Visual Basic.  
  
```vb  
<ServiceContract()> _
Public Interface IExplicitProtectionLevelSampleService
    <OperationContract()> _
    Public Function GetString() As String
    End Function
  
    <OperationContract(ProtectionLevel := ProtectionLevel.None)> _
    Public Function GetInt() As Integer
    End Function
  
    <OperationContractAttribute(ProtectionLevel := ProtectionLevel.EncryptAndSign)> _
    Public Function GetGuid() As Integer
    End Function
  
End Interface  
```  
  
 Služba, která implementuje `IExplicitProtectionLevelSampleService` tuto smlouvu a <xref:System.ServiceModel.WSHttpBinding> má koncový <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>bod, <xref:System.ServiceModel.SecurityMode.Message>který používá výchozí (výchozí , což je ) má následující chování:  
  
- Zprávy `GetString` o operacích jsou šifrovány a podepsány.  
  
- Zprávy `GetInt` operace jsou odesílány jako nešifrovaný a nepodepsaný (tj. prostý) text.  
  
- Operace `GetGuid` <xref:System.Guid?displayProperty=nameWithType> je vrácena ve zprávě, která je zašifrována a podepsána.  
  
 Další informace o úrovních ochrany a jejich použití naleznete v [tématu Principy úrovně ochrany](understanding-protection-level.md). Další informace o zabezpečení naleznete v tématu [Zabezpečení služeb](securing-services.md).  
  
##### <a name="other-operation-signature-requirements"></a>Další požadavky na podpis operace  
 Některé funkce aplikace vyžadují určitý druh podpisu operace. Například vazba <xref:System.ServiceModel.NetMsmqBinding> podporuje trvalé služby a klienty, ve kterém aplikace můžete restartovat uprostřed komunikace a pokračovat tam, kde skončil bez chybějících zpráv. (Další informace naleznete [v tématu Fronty v WCF](./feature-details/queues-in-wcf.md).) Trvalé operace však musí `in` trvat pouze jeden parametr a nemají žádnou vrácenou hodnotu.  
  
 Dalším příkladem je <xref:System.IO.Stream> použití typů v operacích. Vzhledem <xref:System.IO.Stream> k tomu, že parametr obsahuje celé tělo zprávy, `out` pokud je zadán vstup nebo <xref:System.IO.Stream>výstup (tj. `ref` parametr, parametr nebo vrácená hodnota) , musí být jediným vstupem nebo výstupem určeným v operaci. Kromě toho musí být parametr nebo <xref:System.IO.Stream> <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>návratový <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>typ buď , nebo . Další informace o datových proudech naleznete v [tématu Velká data a datové přenosy](./feature-details/large-data-and-streaming.md).  
  
##### <a name="names-namespaces-and-obfuscation"></a>Názvy, obory názvů a zamlžení  
 Názvy a obory názvů typů .NET v definici smluv a operací jsou významné při převodu smluv na WSDL a při vytváření a odeslání zpráv smlouvy. Proto důrazně doporučujeme, aby názvy servisních smluv a `Name` `Namespace` obory názvů byly explicitně nastaveny pomocí vlastností a všech atributů podpůrné <xref:System.ServiceModel.ServiceContractAttribute>smlouvy, <xref:System.ServiceModel.OperationContractAttribute>jako jsou například atributy , <xref:System.Runtime.Serialization.DataContractAttribute>, <xref:System.Runtime.Serialization.DataMemberAttribute>, a další atributy smlouvy.  
  
 Jedním z výsledků je, že pokud názvy a obory názvů nejsou explicitně nastaveny, použití obfuskace IL v sestavení změní názvy typů smlouvy a obory názvů a výsledkem jsou upravené wsdl a drátové výměny, které obvykle selžou. Pokud nenastavíte názvy smluv a obory názvů explicitně, ale <xref:System.Reflection.ObfuscationAttribute> <xref:System.Reflection.ObfuscateAssemblyAttribute> máte v úmyslu použít obfuskaci, použijte atributy a, abyste zabránili změně názvů typů a oborů názvů smlouvy.  
  
## <a name="see-also"></a>Viz také

- [Postupy: Vytvoření kontraktu žádosti a odpovědi](./feature-details/how-to-create-a-request-reply-contract.md)
- [Postupy: Vytvoření jednosměrného kontraktu](./feature-details/how-to-create-a-one-way-contract.md)
- [Postupy: Vytvoření duplexního kontraktu](./feature-details/how-to-create-a-duplex-contract.md)
- [Určování přenosu dat v kontraktech služby](./feature-details/specifying-data-transfer-in-service-contracts.md)
- [Určování a zpracování chyb v kontraktech a službách](specifying-and-handling-faults-in-contracts-and-services.md)
- [Použití relací](using-sessions.md)
- [Synchronní a asynchronní operace](synchronous-and-asynchronous-operations.md)
- [Reliable Services](reliable-services.md)
- [Služby a transakce](services-and-transactions.md)
