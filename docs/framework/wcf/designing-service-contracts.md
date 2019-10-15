---
title: Navrhování kontraktů služby
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF]
ms.assetid: 8e89cbb9-ac84-4f0d-85ef-0eb6be0022fd
ms.openlocfilehash: 27f867bbf079c2e202d93425ddb951fc0df7784a
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72318383"
---
# <a name="designing-service-contracts"></a>Navrhování kontraktů služby
Toto téma popisuje, jaké kontrakty služeb jsou, jak jsou definované, jaké operace jsou k dispozici (a důsledky pro výměny základních zpráv), jaké typy dat se používají, a další problémy, které vám pomůžou s návrhem operací, které splňují požadavky vašeho scénáře.  
  
## <a name="creating-a-service-contract"></a>Vytvoření kontraktu služby  
 Služby zveřejňují určitý počet operací. V aplikacích Windows Communication Foundation (WCF) definujte operace vytvořením metody a jejím označením pomocí atributu <xref:System.ServiceModel.OperationContractAttribute>. Pak, pokud chcete vytvořit kontrakt služby, seskupte vaše operace, buď jejich deklarováním v rámci rozhraní označeného atributem <xref:System.ServiceModel.ServiceContractAttribute>, nebo jejich definováním ve třídě označené stejným atributem. (Základní příklad naleznete v tématu [How to: define a Service kontrakt](how-to-define-a-wcf-service-contract.md).)  
  
 Jakékoli metody, které nemají atribut <xref:System.ServiceModel.OperationContractAttribute>, nejsou operacemi služby a nejsou vystavené službami WCF.  
  
 Toto téma popisuje následující rozhodovací body při navrhování kontraktu služby:  
  
- Zda použít třídy nebo rozhraní.  
  
- Jak určit typy dat, které chcete vyměňovat.  
  
- Typy vzorů Exchange, které můžete použít.  
  
- Zda můžete v rámci smlouvy provádět explicitní požadavky na zabezpečení.  
  
- Omezení pro vstupy a výstupy operací.  
  
## <a name="classes-or-interfaces"></a>Třídy nebo rozhraní  
 Třídy i rozhraní reprezentují seskupení funkcí, a proto obojí lze použít k definování kontraktu služby WCF. Doporučuje se ale používat rozhraní, protože přímo modelují kontrakty služeb. Bez implementace rozhraní nezpůsobí více definovat seskupení metod s určitými podpisy. Implementujte rozhraní kontraktu služby a implementujete službu WCF.  
  
 Všechny výhody spravovaných rozhraní se vztahují na rozhraní kontraktů služeb:  
  
- Rozhraní kontraktu služby můžou roztáhnout libovolný počet dalších rozhraní kontraktu služby.  
  
- Jedna třída může implementovat libovolný počet kontraktů služby implementací těchto servisních kontraktů.  
  
- Implementaci kontraktu služby můžete změnit tak, že změníte implementaci rozhraní, zatímco kontrakt služby zůstane stejný.  
  
- Službu můžete pokaždé naverzi implementovat pomocí starého rozhraní a nového. Starší klienti se připojují k původní verzi, zatímco novější klienti se mohou připojit k novější verzi.  
  
> [!NOTE]
> Při dědění z jiných rozhraní kontraktu služby nemůžete vlastnosti operace přepsat, jako je název nebo obor názvů. Pokud se o to pokusíte, vytvoříte novou operaci v aktuální kontraktu služby.  
  
 Příklad použití rozhraní k vytvoření kontraktu služby najdete v tématu [Postupy: vytvoření služby pomocí rozhraní kontraktu](./feature-details/how-to-create-a-service-with-a-contract-interface.md).  
  
 Můžete ale použít třídu k definování kontraktu služby a implementaci této smlouvy ve stejnou dobu. Výhoda vytváření služeb pomocí <xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.OperationContractAttribute> přímo ke třídě a metodám třídy, v uvedeném pořadí, je rychlost a jednoduchost. Nevýhody jsou tyto spravované třídy, které nepodporují vícenásobnou dědičnost, a v důsledku toho mohou implementovat pouze jeden kontrakt služby najednou. Kromě toho jakákoli změna signatur třídy nebo metody mění veřejný kontrakt pro danou službu, což může zabránit nezměněným klientům v používání vaší služby. Další informace najdete v tématu [implementace kontraktů služeb](implementing-service-contracts.md).  
  
 Příklad, který používá třídu k vytvoření kontraktu služby a implementuje ji ve stejnou dobu, naleznete v tématu [How to: Create a Service with a Contract Class](./feature-details/how-to-create-a-wcf-contract-with-a-class.md).  
  
 V tuto chvíli byste měli pochopit rozdíl mezi definováním kontraktu služby pomocí rozhraní a pomocí třídy. Dalším krokem je rozhodování o tom, jaká data se dají mezi službou a jejími klienty předat zpátky a zpátky.  
  
## <a name="parameters-and-return-values"></a>Parametry a návratové hodnoty  
 Každá operace má návratovou hodnotu a parametr i v případě, že jsou `void`. Nicméně na rozdíl od místní metody, ve které můžete předat odkazy na objekty z jednoho objektu na jiný, operace služby přecházejí na objekty. Místo toho předávají kopie objektů.  
  
 To je důležité, protože každý typ použitý v parametru nebo návratová hodnota musí být serializovatelný; To znamená, že musí být možné převést objekt daného typu na datový proud bajtů a z datového proudu bajtů do objektu.  
  
 Primitivní typy jsou ve výchozím nastavení serializovatelný, stejně jako mnoho typů v .NET Framework.  
  
> [!NOTE]
> Hodnota názvů parametrů v signatuře operace je součástí kontraktu a rozlišuje velká a malá písmena. Pokud chcete použít stejný název parametru místně, ale upravit název v publikovaných metadatech, přečtěte si část <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>.  
  
#### <a name="data-contracts"></a>Kontrakty dat  
 Aplikace orientované na služby, jako jsou aplikace Windows Communication Foundation (WCF), jsou navržené tak, aby spolupracovaly s nejširším možným počtem klientských aplikací na platformách Microsoftu i jiných společností než Microsoft. V rámci nejširší možné interoperability se doporučuje označit typy pomocí atributů <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> k vytvoření kontraktu dat, což je část kontraktu služby, která popisuje data, která vaše provozní operace vyměňuje.  
  
 Kontrakty dat jsou výslovným souhlasem se stylem smlouvy: není-li explicitně použit atribut kontraktu dat, není serializován žádný typ nebo datový člen. Kontrakty dat nesouvisejí s oborem přístupu spravovaného kódu: soukromé datové členy lze serializovat a odesílat jinde, aby k nim měli přístup veřejně. (Základní příklad kontraktu dat najdete v tématu [Postup: Vytvoření základní kontraktu dat pro třídu nebo strukturu](./feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md).) WCF zpracovává definici podkladových zpráv SOAP, které umožňují funkci operace, i serializaci datových typů do těla zprávy a z něj. Pokud jsou vaše datové typy serializovatelné, nemusíte při navrhování Vašich operací myslet na základní infrastrukturu výměny zpráv.  
  
 I když Typická aplikace WCF používá atributy <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> k vytváření kontraktů dat pro operace, můžete použít jiné mechanismy serializace. Standardní mechanismy <xref:System.Runtime.Serialization.ISerializable>, <xref:System.SerializableAttribute> a <xref:System.Xml.Serialization.IXmlSerializable> fungují pro zpracování serializace datových typů do podkladových zpráv SOAP, které je přenesou z jedné aplikace do jiné. Můžete využít více strategií serializace, pokud vaše datové typy vyžadují speciální podporu. Další informace o volbách pro serializaci datových typů v aplikacích WCF najdete v tématu [určení přenos dat v kontraktech služeb](./feature-details/specifying-data-transfer-in-service-contracts.md).  
  
#### <a name="mapping-parameters-and-return-values-to-message-exchanges"></a>Mapování parametrů a návratových hodnot na výměny zpráv  
 Operace služby jsou podporovány základní výměnou zpráv SOAP, které kromě dat vyžadovaných aplikací podporují určité standardní funkce související se zabezpečením, transakcí a relací. Vzhledem k tomu, že se jedná o tento případ, signatura operace služby nadiktují určitý základní *vzor výměny zpráv* (MEP), který může podporovat přenos dat a funkce, které vyžaduje operace. V programovacím modelu WCF můžete zadat tři vzory: požadavky, reakce, jednosměrné a duplexní vzory zpráv.  
  
##### <a name="requestreply"></a>Požadavek nebo odpověď  
 Vzor žádosti nebo odpovědi je ten, ve kterém odesílatel požadavku (klientská aplikace) obdrží odpověď, se kterou je požadavek korelační. Toto je výchozí MEP, protože podporuje operaci, ve které je předán jeden nebo více parametrů k operaci a návratová hodnota je předána zpět volajícímu. Například následující C# příklad kódu ukazuje základní operaci služby, která přijímá jeden řetězec a vrací řetězec.  
  
```csharp  
[OperationContractAttribute]  
string Hello(string greeting);  
```  
  
 Následuje ekvivalentní kód Visual Basic.  
  
```vb  
<OperationContractAttribute()>  
Function Hello (ByVal greeting As String) As String  
```  
  
 Tento podpis operace určuje formu základního výměny zpráv. Pokud žádná korelace neexistuje, WCF nemůže určit, jakou operaci má vrácená hodnota.  
  
 Všimněte si, že pokud neurčíte jiný nadřízený vzor zprávy, jedná se o výměnu zpráv žádostí a odpovědí, a to ani operace služby, které vracejí `void` (`Nothing` v Visual Basic). Výsledkem vaší operace je to, že pokud klient asynchronní operaci neaktivuje, zastaví zpracování, dokud neobdrží návratovou zprávu, a to i v případě, že je tato zpráva v normálním případě prázdná. Následující C# příklad kódu ukazuje operaci, která nevrátí, dokud klient neobdrží prázdnou zprávu v odpovědi.  
  
```csharp  
[OperationContractAttribute]  
void Hello(string greeting);  
```  
  
 Následuje ekvivalentní kód Visual Basic.  
  
```vb  
<OperationContractAttribute()>  
Sub Hello (ByVal greeting As String)  
```  
  
 Předchozí příklad může zpomalit výkon a rychlost odezvy klienta, pokud je operace trvat dlouhou dobu, ale výhody pro požadavky na žádosti a odpověď jsou i při návratu `void`. Nejzjevnější je, že chyby protokolu SOAP mohou být vráceny ve zprávě odpovědi, což znamená, že došlo k nějaké chybě související se službou, ať už v komunikaci nebo zpracování. Chyby protokolu SOAP, které jsou zadány v kontraktu služby, jsou předány klientovi aplikace jako objekt <xref:System.ServiceModel.FaultException%601>, kde parametr typu je typ určený v kontraktu služby. Díky tomu jsou klienti upozorňováni na chybové stavy ve službách WCF. Další informace o výjimkách, chybách protokolu SOAP a zpracování chyb najdete v tématu [určení a zpracování chyb v kontraktech a službách](specifying-and-handling-faults-in-contracts-and-services.md). Příklad služby Request/Reply a klienta najdete v tématu [Postupy: Vytvoření kontraktu požadavku a odpovědi](./feature-details/how-to-create-a-request-reply-contract.md). Další informace o problémech se vzorem požadavek-odpověď najdete v tématu [služby požadavek-odpověď](./feature-details/request-reply-services.md).  
  
##### <a name="one-way"></a>Jednosměrnou metodou  
 Pokud klient aplikace služby WCF by neměl čekat na dokončení operace a nezpracovává chyby protokolu SOAP, může operace zadat jednosměrný vzor zprávy. Jednosměrná operace je ta, ve které klient vyvolá operaci a pokračuje v zpracování poté, co WCF zapíše zprávu do sítě. Obvykle to znamená, že pokud nejsou data odesílaná v odchozí zprávě extrémně velká, klient pokračuje v běhu téměř okamžitě (Pokud při posílání dat nedojde k chybě). Tento typ vzoru výměny zpráv podporuje chování podobné událostem z klienta do aplikace služby.  
  
 Výměna zpráv, ve které je odeslána jedna zpráva a žádná přijata, nemůže podporovat operaci služby, která určuje návratovou hodnotu jinou než `void`; v tomto případě je vyvolána výjimka <xref:System.InvalidOperationException>.  
  
 Žádná návratová zpráva také znamená, že nemůžete vrátit žádnou chybu SOAP, která by označovala chyby při zpracování nebo komunikaci. (Komunikace informací o chybách v případě, že operace jsou jednosměrné operace vyžadují vzor pro výměnu duplexních zpráv.)  
  
 Chcete-li zadat jednosměrnou výměnu zpráv pro operaci, která vrací hodnotu `void`, nastavte vlastnost <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> na hodnotu `true`, jak je uvedeno C# v následujícím příkladu kódu.  
  
```csharp  
[OperationContractAttribute(IsOneWay=true)]  
void Hello(string greeting);  
```  
  
 Následuje ekvivalentní kód Visual Basic.  
  
```vb  
<OperationContractAttribute(IsOneWay := True)>  
Sub Hello (ByVal greeting As String)  
```  
  
 Tato metoda je stejná jako předchozí příklad žádosti nebo odpovědi, ale nastavením vlastnosti <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> na `true` znamená, že i když je metoda shodná, operace služby neodešle návratovou zprávu a klienti se vrátí hned po odchozím odeslání. Zpráva byla předána do vrstvy kanálu. Příklad naleznete v tématu [How to: Create a jednosměrný kontrakt](./feature-details/how-to-create-a-one-way-contract.md). Další informace o jednosměrovém vzoru najdete v tématu [jednosměrné služby](./feature-details/one-way-services.md).  
  
##### <a name="duplex"></a>Duplex  
 Duplexní vzorek je charakterizován schopností služby i klienta, aby odesílal zprávy vzájemně nezávisle na tom, zda používají jednosměrné nebo žádosti nebo zasílání zpráv o odezvě. Tato forma obousměrné komunikace je užitečná pro služby, které musí komunikovat přímo s klientem, nebo poskytovat asynchronní prostředí pro jednu stranu výměny zpráv, včetně chování podobného události.  
  
 Duplexní vzorek je mírně složitější než požadavek, odpověď nebo jednosměrná vzor, protože je k dispozici další mechanismus pro komunikaci s klientem.  
  
 Pro návrh oboustranné smlouvy musíte také navrhnout kontrakt zpětného volání a přiřadit typ tohoto kontraktu zpětného volání vlastnosti <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> atributu <xref:System.ServiceModel.ServiceContractAttribute>, který označuje kontrakt služby.  
  
 Chcete-li implementovat duplexní vzorek, je nutné vytvořit druhé rozhraní, které obsahuje deklarace metod, které jsou volány na klientovi.  
  
 Příklad vytvoření služby a klienta, který přistupuje k této službě, najdete v tématu [Postupy: Vytvoření duplexního kontraktu](./feature-details/how-to-create-a-duplex-contract.md) a [Postup: přístup ke službám pomocí duplexního kontraktu](./feature-details/how-to-access-services-with-a-duplex-contract.md). Pracovní ukázku najdete v tématu [duplexní režim](./samples/duplex.md). Další informace o problémech využívajících duplexní kontrakty najdete v tématu [duplexní služby](./feature-details/duplex-services.md).  
  
> [!CAUTION]
> Když služba obdrží duplexní zprávu, vyhledá v této příchozí zprávě prvek `ReplyTo` a určí, kam se má odpověď odeslat. Pokud kanál, který se používá k přijetí zprávy, není zabezpečený, může nedůvěryhodný klient odeslat škodlivou zprávu s cílovým počítačem `ReplyTo`, což vedlo k odepření služby (DOS) daného cílového počítače.  
  
##### <a name="out-and-ref-parameters"></a>Parametry out a ref  
 Ve většině případů můžete použít parametry `in` (`ByVal` v Visual Basic) a parametry `out` a `ref` (`ByRef` v Visual Basic). Vzhledem k tomu, že parametry `out` i `ref` označují, že se data vracejí z operace, signatura operace, jako je třeba následující, určuje, že se vyžaduje operace požadavku/odpovědi, i když signatura operace vrátí `void`.  
  
```csharp  
[ServiceContractAttribute]  
public interface IMyContract  
{  
  [OperationContractAttribute]  
  public void PopulateData(ref CustomDataType data);  
}  
```  
  
 Následuje ekvivalentní kód Visual Basic.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface IMyContract  
  <OperationContractAttribute()> _  
  Public Sub PopulateData(ByRef data As CustomDataType)  
End Interface  
```  
  
 Jedinou výjimkou jsou případy, kdy váš podpis má konkrétní strukturu. Můžete například použít vazbu <xref:System.ServiceModel.NetMsmqBinding> ke komunikaci s klienty pouze v případě, že metoda použitá k deklaraci operace vrátí `void`; nesmí existovat žádná výstupní hodnota, ať už se jedná o návratovou hodnotu, `ref` nebo parametr `out`.  
  
 Kromě toho použití parametrů `out` nebo `ref` vyžaduje, aby operace měla podkladovou zprávu odpovědi k převedení změněného objektu. Pokud je vaše operace jednosměrnou operací, je vyvolána výjimka <xref:System.InvalidOperationException> za běhu.  
  
### <a name="specify-message-protection-level-on-the-contract"></a>Zadat úroveň ochrany zprávy ve smlouvě  
 Při navrhování vaší smlouvy musíte také určit úroveň ochrany zpráv služeb, které implementují vaši smlouvu. To je nezbytné jenom v případě, že se na vazbu v koncovém bodě smlouvy používá zabezpečení zpráv. Pokud má vazba vypnutou úroveň zabezpečení (to znamená, pokud sada vazby zadaná systémem nastaví <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> na hodnotu <xref:System.ServiceModel.SecurityMode.None?displayProperty=nameWithType>), nebudete se muset rozhodnout na úrovni ochrany zprávy pro daný kontrakt. Ve většině případů se systémem poskytované vazby s použitím zabezpečení na úrovni zprávy poskytují dostatečnou úroveň ochrany a nemusíte uvažovat o úrovni ochrany pro každou operaci nebo pro každou zprávu.  
  
 Úroveň ochrany je hodnota, která určuje, zda jsou zprávy (nebo části zpráv), které podporují službu, podepsané, podepsané a šifrované nebo odesílané bez signatur nebo šifrování. Úroveň ochrany lze nastavit v různých oborech: na úrovni služby, pro určitou operaci, pro zprávu v této operaci nebo na část zprávy. Hodnoty nastavené v jednom oboru se stanou výchozími hodnotami pro menší obory, pokud nejsou explicitně přepsány. Pokud konfigurace vazby nemůže poskytnout požadovanou minimální úroveň ochrany pro kontrakt, je vyvolána výjimka. A v případě, že žádné hodnoty úrovně ochrany nejsou explicitně nastavené u kontraktu, konfigurace vazby řídí úroveň ochrany pro všechny zprávy, pokud vazba obsahuje zabezpečení zpráv. Toto je výchozí chování.  
  
> [!IMPORTANT]
> Rozhodnutí o explicitním nastavení různých rozsahů kontraktu na nižší úrovni, než je úroveň úplné ochrany <xref:System.Net.Security.ProtectionLevel.EncryptAndSign?displayProperty=nameWithType>, je obecně rozhodnutím, že pro zvýšení výkonu zabezpečí určitý stupeň zabezpečení. V těchto případech musí vaše rozhodnutí obejít vaše operace a hodnotu dat, která si vyměňují. Další informace najdete v tématu [zabezpečení služeb](securing-services.md).  
  
 Například následující příklad kódu nenastaví buď vlastnost <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A>, nebo vlastnost <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> u kontraktu.  
  
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
  
 Následuje ekvivalentní kód Visual Basic.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface ISampleService  
  
  <OperationContractAttribute()> _  
  Public Function GetString()As String  
  
  <OperationContractAttribute()> _  
  Public Function GetData() As Integer  
  
End Interface  
```  
  
 Při interakci s implementací `ISampleService` v koncovém bodě s výchozím <xref:System.ServiceModel.WSHttpBinding> (výchozí <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, která je <xref:System.ServiceModel.SecurityMode.Message>) jsou všechny zprávy zašifrované a podepsané, protože se jedná o výchozí úroveň ochrany. Pokud je však služba `ISampleService` použita s výchozím <xref:System.ServiceModel.BasicHttpBinding> (výchozí <xref:System.ServiceModel.SecurityMode>, která je <xref:System.ServiceModel.SecurityMode.None>), odesílají se všechny zprávy jako text, protože pro tuto vazbu není k dispozici žádné zabezpečení a úroveň ochrany bude ignorována (to znamená, že zprávy nejsou šifrovány. bez znaménka). Pokud byl <xref:System.ServiceModel.SecurityMode> změněn na <xref:System.ServiceModel.SecurityMode.Message>, budou tyto zprávy zašifrovány a podepsány (protože by se teď jednalo o výchozí úroveň ochrany vazby).  
  
 Pokud chcete explicitně zadat nebo upravit požadavky na ochranu pro svůj kontrakt, nastavte vlastnost <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> (nebo jakékoli vlastnosti `ProtectionLevel` v menším rozsahu) na úroveň, kterou kontrakt služby vyžaduje. V takovém případě použití explicitního nastavení vyžaduje, aby vazba podporovala toto nastavení minimálně pro použitý obor. Například následující příklad kódu určuje jednu hodnotu <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> explicitně pro operaci `GetGuid`.  
  
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
  
 Následuje ekvivalentní kód Visual Basic.  
  
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
  
 Služba, která implementuje tento @no__t kontraktu-0 a má koncový bod, který používá výchozí <xref:System.ServiceModel.WSHttpBinding> (výchozí <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, která je <xref:System.ServiceModel.SecurityMode.Message>), má následující chování:  
  
- Zprávy operace `GetString` jsou zašifrovány a podepsány.  
  
- Zprávy o operacích `GetInt` se odesílají jako nešifrované a nepodepsaný (což je prostý) text.  
  
- Operace `GetGuid` <xref:System.Guid?displayProperty=nameWithType> se vrátí do zprávy, která je šifrovaná a podepsaná.  
  
 Další informace o úrovních ochrany a způsobu jejich použití najdete v tématu [Principy úrovně ochrany](understanding-protection-level.md). Další informace o zabezpečení najdete v tématu [zabezpečení služeb](securing-services.md).  
  
##### <a name="other-operation-signature-requirements"></a>Požadavky na signatury jiných operací  
 Některé funkce aplikace vyžadují konkrétní druh signatury operace. Například vazba <xref:System.ServiceModel.NetMsmqBinding> podporuje trvalé služby a klienty, ve kterých se aplikace může restartovat v polovině komunikace a v případě, že skončila bez jakýchkoli zpráv, vybrala tam, kde byla vypnuta. (Další informace najdete v tématu [fronty v WCF](./feature-details/queues-in-wcf.md).) Trvalé operace však musí mít pouze jeden parametr `in` a nesmí mít žádnou návratovou hodnotu.  
  
 Dalším příkladem je použití typů <xref:System.IO.Stream> v operacích. Vzhledem k tomu, že parametr <xref:System.IO.Stream> obsahuje celé tělo zprávy, pokud je vstup nebo výstup (tj. parametr `ref`, parametr `out` nebo návratová hodnota) typu <xref:System.IO.Stream>, musí se jednat o jediný vstup nebo výstup zadaný v rámci vaší operace. Kromě toho musí být parametr nebo návratový typ buď <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType> nebo <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>. Další informace o datových proudech najdete v tématu [velké objemy dat a streamování](./feature-details/large-data-and-streaming.md).  
  
##### <a name="names-namespaces-and-obfuscation"></a>Názvy, obory názvů a zmatení  
 Názvy a obory názvů typů .NET v definici smluv a operací jsou významné při převodu smluv na WSDL a při vytváření a posílání zpráv smluv. Proto se důrazně doporučuje, aby názvy kontraktů služby a obory názvů byly explicitně nastaveny pomocí vlastností `Name` a `Namespace` všech pomocných atributů kontraktu, jako jsou <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, <xref:System.Runtime.Serialization.DataContractAttribute>, <xref:System.Runtime.Serialization.DataMemberAttribute> a další smlouva. atribut.  
  
 Z tohoto důvodu je to, že pokud názvy a obory názvů nejsou explicitně nastaveny, použití nezmatené vlastnosti v sestavení mění názvy a obory názvů typu kontraktu a výsledky v upravených výměnách WSDL a drátů, které se obvykle nezdaří. Pokud názvy kontraktů a obory názvů explicitně nenastavíte, ale hodláte použít zmatení, použijte atributy <xref:System.Reflection.ObfuscationAttribute> a <xref:System.Reflection.ObfuscateAssemblyAttribute>, abyste zabránili úpravám názvů typů kontraktů a oborů názvů.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření kontraktu žádosti a odpovědi](./feature-details/how-to-create-a-request-reply-contract.md)
- [Postupy: Vytvoření jednosměrného kontraktu](./feature-details/how-to-create-a-one-way-contract.md)
- [Postupy: Vytvoření duplexního kontraktu](./feature-details/how-to-create-a-duplex-contract.md)
- [Určování přenosu dat v kontraktech služby](./feature-details/specifying-data-transfer-in-service-contracts.md)
- [Určování a zpracování chyb v kontraktech a službách](specifying-and-handling-faults-in-contracts-and-services.md)
- [Použití relací](using-sessions.md)
- [Synchronní a asynchronní operace](synchronous-and-asynchronous-operations.md)
- [Spolehlivé služby](reliable-services.md)
- [Služby a transakce](services-and-transactions.md)
