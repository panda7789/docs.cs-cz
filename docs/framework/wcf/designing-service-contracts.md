---
title: Navrhování kontraktů služby
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service contracts [WCF]
ms.assetid: 8e89cbb9-ac84-4f0d-85ef-0eb6be0022fd
ms.openlocfilehash: 68ea866b736350b8a393d1f4788e4b08754e5ab4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785031"
---
# <a name="designing-service-contracts"></a>Navrhování kontraktů služby
Toto téma popisuje, jakou servisní smlouvy se, jak jsou definovány, jaké operace jsou k dispozici (a důsledky pro základní výměny zpráv), jaké typy dat jsou používané a dalších problémů, které vám pomůžou navrhnout operace, které splňují požadavky na váš scénář.  
  
## <a name="creating-a-service-contract"></a>Vytvoření kontraktu služby  
 Služby vystavují počet operací. V aplikacích Windows Communication Foundation (WCF), definují operace tak, že vytvoření metody a označit ji atributem <xref:System.ServiceModel.OperationContractAttribute> atribut. Potom vytvořte smlouvy o poskytování služeb, seskupit dohromady vaše operace, buď deklarací v rámci rozhraní označené <xref:System.ServiceModel.ServiceContractAttribute> atribut, nebo je podle definice ve třídě s atributem stejné. (Základní příklad naleznete v tématu [jak: Definování kontraktu služby](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).)  
  
 Všechny metody, které nemají <xref:System.ServiceModel.OperationContractAttribute> atributu nejsou operace služby a nejsou přístupné služby WCF services.  
  
 Toto téma popisuje následující body rozhodnutí při navrhování kontraktu služby:  
  
- Určuje, zda použít třídy nebo rozhraní.  
  
- Jak určit typy dat, které chcete k exchangi.  
  
- Typy exchange vzory, které můžete použít.  
  
- Určuje, zda můžete provést explicitní zabezpečení požadavky součástí kontraktu.  
  
- Omezení pro operace vstupy a výstupy.  
  
## <a name="classes-or-interfaces"></a>Třídy nebo rozhraní  
 Třídy a rozhraní představují seskupení funkce, a proto i slouží k definování kontraktu služby WCF. Doporučujeme však použít rozhraní, protože kontraktů služby modelují přímo. Bez implementace rozhraní definovat více než seskupení s určitým podpisy metod. Implementovat rozhraní kontraktu služby a implementovali služby WCF.  
  
 Všechny výhody spravovaných rozhraních aplikována na rozhraní kontraktu služby:  
  
- Rozhraní kontraktu služby můžete rozšířit libovolný počet dalších rozhraní kontraktu služby.  
  
- Jeden třída může implementovat libovolný počet kontrakty služeb díky implementaci těchto rozhraní kontraktu služby.  
  
- Implementace kontraktu služby můžete upravit tak, že změníte implementace rozhraní, zatímco kontrakt služby zůstává stejná.  
  
- Verze můžete prostřednictvím implementace rozhraní staré a nové služby. Staré klienti připojovat k původní verzi, zatímco novějších klientů může připojit k novější verzi.  
  
> [!NOTE]
>  Při dědění z jiných rozhraní kontraktu služby, nelze přepsat vlastnosti operace, jako je název nebo obor názvů. Pokud se pokusíte k tomu, vytvoříte novou operaci v aktuální kontraktu služby.  
  
 Příklad použití rozhraní pro vytvoření kontraktu a služby, najdete v části [jak: Vytvoření služby pomocí rozhraní kontraktu](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md).  
  
 Ale můžete třídu a definování kontraktu služby ve stejnou dobu implementace tohoto kontraktu. Výhoda vytváření vašich služeb s použitím <xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.OperationContractAttribute> přímo třídy a metody ve třídě, je rychlosti a jednoduchost. Nevýhodou je, že spravované třídy nepodporují vícenásobnou dědičnost a díky tomu mohou pouze implementovat jeden kontrakt služby najednou. Kromě toho všechny změny třídy nebo metody podpisy upraví veřejný kontrakt pro tuto službu, která bez úprav klientům zabránit používání služby. Další informace najdete v tématu [implementace kontraktů služeb](../../../docs/framework/wcf/implementing-service-contracts.md).  
  
 Příklad, který používá třída pro vytvoření kontraktu služby a implementuje ve stejnou dobu, naleznete v tématu [jak: Vytvoření služby s třídou kontraktu](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md).  
  
 V tomto okamžiku by měla pochopit rozdíl mezi definování vašich kontrakt služby s použitím rozhraní a pomocí třídy. Dalším krokem je rozhodování o tom, jaká data lze předat vpřed a zpět mezi službou a klienty.  
  
## <a name="parameters-and-return-values"></a>Parametry a návratové hodnoty  
 Každá operace má návratovou hodnotu a parametr, i v případě, že jde o `void`. Ale na rozdíl od místní metody, ve kterém můžete předat odkazy na objekty z jednoho objektu do druhého, servisní operace nepředávejte odkazy na objekty. Místo toho předat kopie objekty.  
  
 To je důležité, protože každý typ použit jako parametr nebo návratové hodnoty musí být serializovatelný; To znamená musí být možné převést objekt daného typu do datového proudu bajtů a z datového proudu bajtů do objektu.  
  
 Primitivní typy jsou serializovatelné ve výchozím nastavení, jako jsou mnoho typů v rozhraní .NET Framework.  
  
> [!NOTE]
>  Hodnota názvy parametrů v signatuře operace jsou součástí kontraktu a jsou malá a velká písmena. Pokud chcete používat stejný název parametru místně, ale změňte název v publikovaných metadat, najdete v článku <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>.  
  
#### <a name="data-contracts"></a>Kontrakty dat  
 Aplikace orientované na služby, jako je Windows Communication Foundation (WCF) aplikace jsou navržené pro spolupráci s nejširší počet klientských aplikací na Microsoft a jiné platformy než Microsoft. Pro nejširší možné spolupráci se doporučuje, abyste označili typů s <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> atributy k vytvoření kontraktu dat, které je uvedeno v kontraktu služby, který popisuje data, která servisní operace. Exchange.  
  
 Kontrakty dat jsou smlouvy vyjádřit výslovný souhlas styl: Pokud výslovně atribut kontraktu dat bez typu nebo datový člen serializován. Kontrakty dat nesouvisí s obor přístupu spravovaného kódu: Privátní členy dat lze serializovat a odeslané jinde veřejně přístupná. (Příklad základní kontrakt dat, naleznete v tématu [jak: Vytvoření základního kontraktu dat pro třídu nebo strukturu](../../../docs/framework/wcf/feature-details/how-to-create-a-basic-data-contract-for-a-class-or-structure.md).) WCF zpracovává definici základní zprávy protokolu SOAP, které umožňují funkce operace, jakož i serializace typů dat do a z těla zprávy. Datové typy jsou serializovatelné, není potřeba uvažovat o základní infrastruktury serveru exchange zprávu při navrhování operací.  
  
 I když používá Typická aplikace WCF <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> atributy k vytvoření kontraktů dat pro operace, můžete použít další mechanismy serializace. Standardní <xref:System.Runtime.Serialization.ISerializable>, <xref:System.SerializableAttribute> a <xref:System.Xml.Serialization.IXmlSerializable> mechanismy všechny fungují pro zpracování serializace datové typy do základní zprávy protokolu SOAP, které zajišťují z jedné aplikace do jiného. Pokud vaše typy dat vyžadují speciální podporu, můžete použít další strategie serializace. Další informace o možnostech pro serializaci datových typů aplikací služby WCF, naleznete v tématu [zadání přenosu dat v kontraktech služeb](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).  
  
#### <a name="mapping-parameters-and-return-values-to-message-exchanges"></a>Mapování parametrů a návratové hodnoty pro výměny zpráv  
 Operací služby podporuje základní výměny zpráv SOAP, které přenášejí data aplikací vpřed a zpět, kromě dat vyžadované aplikací pro podporu určitých standard zabezpečení, transakce a funkcím souvisejícím s relace. Protože je to tento případ, Určuje podpis operace služby na určité základní *vzoru výměny zpráv* (MEP), které podporují přenos dat a funkce operace vyžaduje. Můžete určit tři vzory v programovacího modelu WCF: požadavek nebo odpověď, jednosměrné a vzory duplexní zprávy.  
  
##### <a name="requestreply"></a>Žádost odpověď  
 Vzor požadavek nebo odpověď je jedním ve kterém odesílatel požadavku (klientská aplikace) obdrží odpověď, které jsou korelována žádost. Toto je výchozí MEP, protože podporuje operace, ve kterém jeden nebo více parametrů jsou předány operaci a návratová hodnota se předá zpět do volajícího. Například následující C# příklad kódu ukazuje operaci služby na úrovni basic, která přijímá jeden řetězec a vrátí hodnotu typu string.  
  
```csharp  
[OperationContractAttribute]  
string Hello(string greeting);  
```  
  
 Níže je ekvivalentní kódu jazyka Visual Basic.  
  
```vb  
<OperationContractAttribute()>  
Function Hello (ByVal greeting As String) As String  
```  
  
 Tento podpis operace přikazuje formuláři základní výměně zpráv. Pokud žádná korelace, WCF nelze určit pro operaci, která je určená návratovou hodnotu.  
  
 Všimněte si, že pokud zadáte jiný základní vzor zprávu, dokonce i operace služby, které vracejí `void` (`Nothing` v jazyce Visual Basic) jsou výměny zpráv žádost odpověď. Výsledek pro operaci je, že pokud klient asynchronně vyvolá operaci, klient se zastaví zpracovávání, dokud návratovou zprávu přijmout, i když se tato zpráva je prázdná v případě normální. Následující C# příklad kódu ukazuje operaci, která nevrací, dokud klient přijal zprávu prázdnou odpověď.  
  
```csharp  
[OperationContractAttribute]  
void Hello(string greeting);  
```  
  
 Níže je ekvivalentní kódu jazyka Visual Basic.  
  
```vb  
<OperationContractAttribute()>  
Sub Hello (ByVal greeting As String)  
```  
  
 V předchozím příkladu může zpomalit výkon klienta a rychlost odezvy, pokud operace trvá dlouhou dobu provádění, ale existují výhody operace požadavku/odpovědi dokonce i když se vrátí `void`. Nejobvyklejšími je, že mohou být chyb SOAP vrácena ve zprávě s odpovědí, který označuje, že nějaké chyby související se službou došlo v komunikaci nebo zpracování. Klientská aplikace, jako jsou předány chyb SOAP, které jsou uvedeny v servisní smlouvě <xref:System.ServiceModel.FaultException%601> objekt, kde parametr typu je typ zadaný v kontraktu služby. To usnadňuje oznamující klientů o chybové stavy ve službách WCF. Další informace o výjimkách, chyby protokolu SOAP a zpracování chyb, naleznete v tématu [zadání a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md). Příklad požadavku/odpovědi služby a klienta najdete v tématu [jak: Vytvoření kontraktu požadavku a odpovědi](../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md). Další informace o problémech se vzorem požadavek odpověď, naleznete v tématu [služby požadavku a odpovědi](../../../docs/framework/wcf/feature-details/request-reply-services.md).  
  
##### <a name="one-way"></a>Jednosměrná  
 Pokud klienta aplikace služby WCF nesmí čekat na dokončení operace a nezpracovává chyb SOAP, operaci můžete zadat vzor jednosměrná zpráva. Jednosměrná operace je jednou ve kterém klienta vyvolá operaci a bude pokračovat zpracování po WCF zapisuje zprávu do sítě. Obvykle to znamená, že pokud je velmi velkých dat odesílaných v odchozí zprávě klient pokračuje v téměř okamžité spuštění (Pokud dojde k chybě odesílání dat). Tento typ vzoru výměny zpráv podporuje chování podobných událostí z klienta aplikace služby.  
  
 Výměna zpráv, ve které jedna zpráva se odešlou a žádný nemůže podporovat operaci služby, která určuje návratovou hodnotu jiné než `void`; v tomto případě <xref:System.InvalidOperationException> je vyvolána výjimka.  
  
 Žádná vrácená zpráva také znamená, že může být žádné nastala chyba protokolu SOAP vrácena k označení chyby ve zpracování nebo komunikaci. (Vzoru výměny zpráv duplexní komunikaci informace o chybě, když operace jsou Jednosměrná operace vyžaduje.)  
  
 Chcete-li určit exchange jednosměrná zpráva pro operaci, která vrátí `void`, nastavte <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost `true`, jako v následující C# příklad kódu.  
  
```csharp  
[OperationContractAttribute(IsOneWay=true)]  
void Hello(string greeting);  
```  
  
 Níže je ekvivalentní kódu jazyka Visual Basic.  
  
```vb  
<OperationContractAttribute(IsOneWay := True)>  
Sub Hello (ByVal greeting As String)  
```  
  
 Tato metoda je stejný jako předchozí příklad požadavku/odpovědi ale nastavení <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost `true` znamená, že i když je metoda stejné, operace služby neodesílá návratovou zprávu a klienti se vrátí okamžitě jednou do vrstvy kanálu byl předán odchozí zprávy. Příklad najdete v tématu [jak: Vytvoření jednosměrného kontraktu](../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md). Další informace o vzoru jednosměrné, naleznete v tématu [One-Way služby](../../../docs/framework/wcf/feature-details/one-way-services.md).  
  
##### <a name="duplex"></a>Duplex  
 Duplexní vzor charakterizován schopnost služby a klient pro odesílání zpráv k sobě navzájem nezávislé ať už pomocí jednosměrné nebo zasílání zpráv žádost odpověď. Tato forma obousměrná komunikace je užitečné pro služby, které musí komunikovat přímo do klienta nebo pro asynchronní prostředí po obou stranách výměně zpráv, včetně podobně jako události.  
  
 Duplexní vzor je o něco složitější než požadavek/odpověď nebo jednosměrné vzorů z důvodu další mechanismus pro komunikaci s klientem.  
  
 Navrhnout duplexního kontraktu, musí také navrhnout kontrakt zpětného volání a přiřazení typu tohoto kontraktu zpětného volání pro <xref:System.ServiceModel.ServiceContractAttribute.CallbackContract%2A> vlastnost <xref:System.ServiceModel.ServiceContractAttribute> atribut, který označuje váš kontraktu služby.  
  
 K implementaci vzoru duplexní, musíte vytvořit druhý rozhraní obsahující deklarace metody, které jsou volány v klientském počítači.  
  
 Příklad vytvoření služby a klienta, který přistupuje k této službě najdete v tématu [jak: Vytvoření duplexního kontraktu](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md) a [jak: Přístup ke službám pomocí duplexního kontraktu](../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md). Pracovní ukázku najdete v tématu [duplexní](../../../docs/framework/wcf/samples/duplex.md). Další informace o problémech s využitím duplexní kontrakty najdete v tématu [duplexní služby](../../../docs/framework/wcf/feature-details/duplex-services.md).  
  
> [!CAUTION]
>  Když služba obdrží zprávu duplexní, dohlíží na `ReplyTo` elementu v této příchozí zprávy k určení, kam chcete odeslat odpověď. Pokud není zabezpečený kanál, který se používá pro příjem zprávy, pak nedůvěryhodného klienta může odeslat škodlivý zprávu s cílový počítač `ReplyTo`, vedoucí k odepření služby (DOS) tento cílový počítač.  
  
##### <a name="out-and-ref-parameters"></a>Parametry Ref a Out  
 Ve většině případů můžete použít `in` parametry (`ByVal` v jazyce Visual Basic) a `out` a `ref` parametry (`ByRef` v jazyce Visual Basic). Protože obě `out` a `ref` parametrů označuje, že data jsou vrácena z operace, podpis operace, jako je například následující Určuje, že operace požadavku/odpovědi je vyžadována, i když se podpis operace vrátí `void`.  
  
```csharp  
[ServiceContractAttribute]  
public interface IMyContract  
{  
  [OperationContractAttribute]  
  public void PopulateData(ref CustomDataType data);  
}  
```  
  
 Níže je ekvivalentní kódu jazyka Visual Basic.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface IMyContract  
  <OperationContractAttribute()> _  
  Public Sub PopulateData(ByRef data As CustomDataType)  
End Interface  
```  
  
 Jedinou výjimkou jsou případy, ve kterých má svůj podpis danou strukturu. Například můžete použít <xref:System.ServiceModel.NetMsmqBinding> vazby ke komunikaci s klienty pouze tehdy, pokud metoda používá k deklaraci operace vrátí `void`; může existovat žádné výstupní hodnota, zda je návratová hodnota `ref`, nebo `out` parametru.  
  
 Kromě toho pomocí `out` nebo `ref` parametry vyžaduje, aby operace měly základní odpověď zpět provádět změněný objekt. Pokud vaše operace je jednosměrná operace <xref:System.InvalidOperationException> je vyvolána výjimka za běhu.  
  
### <a name="specify-message-protection-level-on-the-contract"></a>Zadejte úroveň ochrany zprávy kontraktu  
 Při navrhování vaší smlouvy, musíte se rovněž rozhodnout úroveň ochrany zprávy služeb, které implementují vaše smlouvy. To je nezbytné pouze v případě, že zabezpečení zprávy se použije pro vazbu v koncovém bodě této smlouvy. Pokud vazba má zabezpečení vypnuto (tj. Pokud vazeb poskytovaných systémem nastaví <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType> na hodnotu <xref:System.ServiceModel.SecurityMode.None?displayProperty=nameWithType>) a není nutné při rozhodování o úroveň ochrany zprávy pro kontrakt. Ve většině případů vazeb poskytovaných systémem pomocí zabezpečení na úrovni zprávy použít poskytnout dostatečnou úroveň ochrany a není nutné vzít v úvahu úrovně ochrany pro každou operaci nebo pro každou zprávu.  
  
 Úroveň ochrany je hodnota, která určuje, zda zprávy (nebo částí zprávy), které podporují službu jsou podepsané, podepsaný a zašifrovaný nebo odeslán bez informace o podpisy nebo šifrování. Úroveň ochrany lze nastavit v různých oborech: Na úrovni služby pro konkrétní operace, zprávy v rámci této operace nebo část zprávy. Pokud explicitně přepisuje se stanou hodnoty nastavené na jeden obor výchozí hodnota pro menší obory. Pokud konfiguraci vazby nelze zadat úroveň ochrany vyžaduje minimální pro kontrakt, je vyvolána výjimka. A když žádné hodnoty pro úroveň ochrany jsou explicitně nastavené ve smlouvě, konfigurace vazby řídí úroveň ochrany pro všechny zprávy, pokud vazby zabezpečení zpráv. Toto je výchozí chování.  
  
> [!IMPORTANT]
>  Rozhodování o tom, zda chcete explicitně nastavit různé obory kontraktu na nižší než úroveň plná ochrana <xref:System.Net.Security.ProtectionLevel.EncryptAndSign?displayProperty=nameWithType> je obecně rozhodnutí, které obchoduje určitý stupeň zabezpečení pro zajištění zvýšeného výkonu. V těchto případech musí vaše rozhodnutí točí kolem operací a hodnota data, která si vyměňují. Další informace najdete v tématu [zabezpečení služby](../../../docs/framework/wcf/securing-services.md).  
  
 Například následující příklad kódu nemá nastaven buď <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> nebo <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> vlastnost kontraktu.  
  
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
  
 Níže je ekvivalentní kódu jazyka Visual Basic.  
  
```vb  
<ServiceContractAttribute()> _  
Public Interface ISampleService  
  
  <OperationContractAttribute()> _  
  Public Function GetString()As String  
  
  <OperationContractAttribute()> _  
  Public Function GetData() As Integer  
  
End Interface  
```  
  
 Při interakci s `ISampleService` implementace v koncovém bodu s výchozím <xref:System.ServiceModel.WSHttpBinding> (výchozí hodnota <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, což je <xref:System.ServiceModel.SecurityMode.Message>), všechny zprávy jsou zašifrované a podepsán, protože to je výchozí úroveň ochrany. Ale, když `ISampleService` služba se používá s výchozím <xref:System.ServiceModel.BasicHttpBinding> (výchozí hodnota <xref:System.ServiceModel.SecurityMode>, což je <xref:System.ServiceModel.SecurityMode.None>), všechny zprávy se odesílají jako text, protože není žádné zabezpečení pro tuto vazbu, a proto ignorovány úroveň ochrany (to znamená, zprávy jsou šifrovaná, ani podepsané). Pokud <xref:System.ServiceModel.SecurityMode> byl změněn na <xref:System.ServiceModel.SecurityMode.Message>, pak by se tyto zprávy zašifrovaná a podepsaná (protože teď, který bude vazby výchozí úroveň ochrany).  
  
 Pokud chcete explicitně zadat nebo upravit požadavky na ochranu pro vaše smlouvy, nastavte <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> vlastnost (nebo některý z `ProtectionLevel` vlastnosti na menší rozsah) na úrovni vyžaduje váš kontraktu služby. V takovém případě pomocí explicitní nastavení vyžaduje, aby připojení pro podporu tohoto nastavení minimálně pro obor použít. Například následující příklad kódu určuje jeden <xref:System.ServiceModel.OperationContractAttribute.ProtectionLevel%2A> hodnotu explicitně, pro `GetGuid` operace.  
  
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
  
 Níže je ekvivalentní kódu jazyka Visual Basic.  
  
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
  
 Služba, která implementuje to `IExplicitProtectionLevelSampleService` smlouvy a má koncový bod, který používá výchozí <xref:System.ServiceModel.WSHttpBinding> (výchozí hodnota <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>, což je <xref:System.ServiceModel.SecurityMode.Message>) má následující chování:  
  
- `GetString` Operace zprávy jsou zašifrovaná a podepsaná.  
  
- `GetInt` Operace zprávy jsou odeslány jako nešifrovaný a bez znaménka (to znamená, plain) text.  
  
- `GetGuid` Operace <xref:System.Guid?displayProperty=nameWithType> se vrátí ve zprávě, která je zašifrovaná a podepsaná.  
  
 Další informace o úrovních ochrany a způsob jejich použití naleznete v tématu [úroveň ochrany Principy](../../../docs/framework/wcf/understanding-protection-level.md). Další informace o zabezpečení najdete v tématu [zabezpečení služby](../../../docs/framework/wcf/securing-services.md).  
  
##### <a name="other-operation-signature-requirements"></a>Další požadavky podpis operace  
 Některé funkce aplikace vyžadují konkrétní druh operace podpisu. Například <xref:System.ServiceModel.NetMsmqBinding> vazba podporuje odolných služeb a klientů, ve kterých můžete aplikaci restartujte uprostřed komunikace a pokračovat tam, kde skončila bez chybí nějaké zprávy. (Další informace najdete v tématu [fronty ve WCF](../../../docs/framework/wcf/feature-details/queues-in-wcf.md).) Trvalý operace ale přijme jenom jeden `in` parametr a nemají žádnou návratovou hodnotu.  
  
 Dalším příkladem je použití <xref:System.IO.Stream> typů v operacích. Protože <xref:System.IO.Stream> parametr zahrnuje obsah celé zprávy, pokud vstup nebo výstup (to znamená, `ref` parametr, `out` parametr nebo návratovou hodnotu) je typu <xref:System.IO.Stream>, pak musí být pouze vstupní nebo výstupní zadané v vaší operace. Kromě toho, parametr nebo návratový typ musí být buď <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>, nebo <xref:System.Xml.Serialization.IXmlSerializable?displayProperty=nameWithType>. Další informace o datových proudů, naleznete v tématu [velkých objemů dat a datových proudů](../../../docs/framework/wcf/feature-details/large-data-and-streaming.md).  
  
##### <a name="names-namespaces-and-obfuscation"></a>Názvy oborů názvů a obfuskace  
 Názvy a obory názvů typů .NET v definici smluv a operace jsou významné po smluv se převedou na WSDL a pokud se vytváří a odesílají zprávy kontraktu. Proto důrazně doporučujeme, že názvy kontraktu služby a obory názvů jsou explicitně nastavené pomocí `Name` a `Namespace` vlastnosti všechny podpůrné smlouvy atributy, jako <xref:System.ServiceModel.ServiceContractAttribute>, <xref:System.ServiceModel.OperationContractAttribute>, <xref:System.Runtime.Serialization.DataContractAttribute>,  <xref:System.Runtime.Serialization.DataMemberAttribute>a další atributy smlouvy.  
  
 Jeden výsledek tohoto je, že pokud nejsou explicitně nastavit názvy a obory názvů, použití IL obfuskace sestavení mění názvy typů kontraktu a obory názvů a upravené WSDL a výměny při přenosu, které obvykle za následek. Pokud není nastaveno smlouvy názvy a obory názvů explicitně, ale v úmyslu použít obfuskace, použijte <xref:System.Reflection.ObfuscationAttribute> a <xref:System.Reflection.ObfuscateAssemblyAttribute> atributů, které mají-li zabránit úpravy kontrakt zadejte názvy a obory názvů.  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření kontraktu požadavku a odpovědi](../../../docs/framework/wcf/feature-details/how-to-create-a-request-reply-contract.md)
- [Postupy: Vytvoření jednosměrného kontraktu](../../../docs/framework/wcf/feature-details/how-to-create-a-one-way-contract.md)
- [Postupy: Vytvoření duplexního kontraktu](../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
- [Určování přenosu dat v kontraktech služby](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
- [Určování a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)
- [Použití relací](../../../docs/framework/wcf/using-sessions.md)
- [Synchronní a asynchronní operace](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
- [Spolehlivé služby](../../../docs/framework/wcf/reliable-services.md)
- [Služby a transakce](../../../docs/framework/wcf/services-and-transactions.md)
