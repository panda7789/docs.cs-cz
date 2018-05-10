---
title: Náhrady kontraktů dat
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], surrogates
ms.assetid: 8c31134c-46c5-4ed7-94af-bab0ac0dfce5
ms.openlocfilehash: b06cb45d6075c8de1da973a11e2edec6792df304
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="data-contract-surrogates"></a>Náhrady kontraktů dat
Kontrakt dat *náhradní* je pokročilá funkce založena na kontrakt dat modelu. Tato funkce je určena pro typ přizpůsobení a nahrazování v situacích, kde chcete změnit, jak je serializováno typu, deserializovat nebo předpokládané do metadata uživatele. Některé scénáře, kde lze použít náhradní je při kontraktu dat nebyl zadán pro typ, pole a vlastnosti nejsou označené jako <xref:System.Runtime.Serialization.DataMemberAttribute> atribut nebo uživatele chcete dynamicky vytvořte variace schématu.  
  
 Serializace a deserializace jsou provést pomocí náhradní kontraktu dat při použití <xref:System.Runtime.Serialization.DataContractSerializer> převést z rozhraní .NET Framework na vhodný formátu, například XML. Náhradní kontraktu dat lze také upravit metadata exportovat za účelem typů, při vytváření reprezentace metadata, jako jsou dokumenty schématu XML (XSD). Po importu kód je vytvořený z metadat a náhradní můžete použít v tomto případě k přizpůsobení bude vygenerovaný kód.  
  
## <a name="how-the-surrogate-works"></a>Jak funguje náhradní  
 Náhradní funguje tak, že jeden typ mapování (typ "původní") na jiný typ (typ "surrogated"). Následující příklad ukazuje původní typ `Inventory` a nové náhradní `InventorySurrogated` typu. `Inventory` Typ není serializovatelný ale `InventorySurrogated` je typu:  
  
 [!code-csharp[C_IDataContractSurrogate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#1)]  
  
 Protože kontrakt dat nebyla definována pro tuto třídu, převeďte na třídu náhradní s kontraktu dat třídy. Surrogated třída je znázorněno v následujícím příkladu:  
  
 [!code-csharp[C_IDataContractSurrogate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#2)]  
  
## <a name="implementing-the-idatacontractsurrogate"></a>Implementace IDataContractSurrogate  
 Pokud chcete použít náhradní kontraktu dat, implementovat <xref:System.Runtime.Serialization.IDataContractSurrogate> rozhraní.  
  
 Následuje přehled každé metody <xref:System.Runtime.Serialization.IDataContractSurrogate> s možnou implementaci.  
  
### <a name="getdatacontracttype"></a>GetDataContractType  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Metoda mapuje jeden typ do jiného. Tato metoda je vyžadována pro serializaci, deserializace, import a export.  
  
 První úlohou je definovat, jaké typy budou namapované na jiné typy. Příklad:  
  
 [!code-csharp[C_IDataContractSurrogate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#3)]  
  
-   V serializaci, tato metoda vrátí mapování následně použitá k transformaci na původní instanci surrogated instanci voláním <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> metoda.  
  
-   U deserializace je k deserializaci do instance typu náhradní mapování vrácená touto metodou používán serializátor. Následně volá <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> k transformaci surrogated instance do instance původní typu.  
  
-   Na exportu se projeví náhradní typ tato metoda vrátí získat kontrakt dat sloužící ke generování metadat.  
  
-   Při importu počáteční typ se změní na náhradní typ, který se projeví získat kontrakt dat pro účely jako odkazující na podporu.  
  
 <xref:System.Type> Parametr je typ objektu, který probíhá serializace, deserializovat, importu nebo exportu. <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Metoda musí vracet typ vstupu, pokud náhradní nezpracovává typu. Jinak vrátí surrogated příslušného typu. Pokud existuje několik typů náhradní, množství mapování lze definovat v této metodě.  
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Metoda není volána pro předdefinované data primitiv kontrakt, jako <xref:System.Int32> nebo <xref:System.String>. Pro ostatní typy, jako je například pole, uživatelem definované typy a jiné datové struktury bude se tato metoda volána pro každý typ.  
  
 V předchozím příkladu metoda ověří, zda `type` parametr a `Inventory` jsou porovnatelný. Pokud ano, metoda mapuje jej do `InventorySurrogated`. Vždy, když serializace, se nazývá deserializace, schéma import nebo export schématu, tato funkce je volána nejprve pro určení mapování mezi typy.  
  
### <a name="getobjecttoserialize-method"></a>GetObjectToSerialize – metoda  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> Metoda převede na původní instanci typu k instanci surrogated typu. Metoda je vyžadována pro serializaci.  
  
 Dalším krokem je určit způsob, jakým fyzické data budou mapována z původní instance na náhradní implementací <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> metoda. Příklad:  
  
 [!code-csharp[C_IDataContractSurrogate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#4)]  
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> Metoda je volána, když je objekt serializován. Tato metoda přenosu dat z původní typ na pole surrogated typu. Pole může být přímo mapována na náhradní baterie pole nebo manipulace původní data mohou být uloženy do náhradní. Některé možné způsoby využití patří: přímého mapování polí, provádění operací na data, která mají být uložené v polích surrogated nebo ukládání XML původní typ v poli surrogated.  
  
 `targetType` Parametr odkazuje na deklarovaný typ člena. Tento parametr je surrogated typ vrácený <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> metoda. Serializátor nevynucuje, zda je objekt vrácený přiřadit k tomuto typu. `obj` Parametr je objekt k serializaci a bude převeden na jeho náhradní v případě potřeby. Tato metoda musí vrátit vstupního objektu, pokud surrogated nezpracovává objektu. Nový objekt náhradní, jinak bude vrácen. Náhradní není volána, pokud objekt má hodnotu null. Řada náhradní mapování pro různé instance může být definován v rámci této metody.  
  
 Při vytváření <xref:System.Runtime.Serialization.DataContractSerializer>, můžete určit, aby ho chcete zachovat odkazy na objekty. (Další informace najdete v tématu [serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).) To se provádí nastavením `preserveObjectReferences` parametr v jeho konstruktor `true`. V takovém případě náhradní je volat pouze jednou pro objekt vzhledem k tomu, že odkaz na všechny následné serializations právě zápisu do datového proudu. Pokud `preserveObjectReferences` je nastaven na `false`, pak náhradní nazývá pokaždé, když je zjištěna instance.  
  
 Pokud typ serializovat instance se liší od deklarovaný typ, jsou informace o typu zapsána do datového proudu, například `xsi:type` umožňující instance rekonstrukce na druhém konci. Tento proces probíhá, zda je objekt surrogated nebo ne.  
  
 V předchozím příkladu převede k datům `Inventory` instance tohoto `InventorySurrogated`. Kterou kontroluje typ objektu a provede nezbytné manipulace převést na typ surrogated. V tomto případě pole `Inventory` třídy se přímo překopírují na `InventorySurrogated` třídy pole.  
  
### <a name="getdeserializedobject-method"></a>GetDeserializedObject – metoda  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> Metoda převede surrogated typu instance na původní instanci typu. Je vyžadována pro deserializaci.  
  
 Dalším krokem je určit způsob, jakým fyzické data budou mapována z instance náhradní do původního. Příklad:  
  
 [!code-csharp[C_IDataContractSurrogate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#5)]  
  
 Tato metoda je volána pouze během deserializace objektu. Poskytuje data zpětné mapování pro deserializace z typu náhradní zpět na původní. Podobně jako `GetObjectToSerialize` metoda, některé možné používá může být přímo výměnu pole dat, provádět operace s daty a ukládat XML data. Při deserializaci, nemusí vždy získat přesné datové hodnoty z původní kvůli manipulace během převodu dat.  
  
 `targetType` Parametr odkazuje na deklarovaný typ člena. Tento parametr je surrogated typ vrácený `GetDataContractType` metoda. `obj` Parametr odkazuje na objekt, který má byla deserializovat. Objekt můžete převést zpět na původní, pokud je surrogated. Tato metoda vrátí vstupního objektu, pokud náhradní nezpracovává objektu. Deserializovaný objekt, jinak bude vrácen, po dokončení jeho převodu. Pokud existuje několik typů náhradní, může poskytovat převod dat z náhradní na primární pro každou tak, že zadáte každý typ a jeho převodu.  
  
 Když se vrátí objekt, jsou aktualizované pro objekt vrácený rutinou tento náhradní vnitřní objekt tabulky. Všechny následné odkazy na instanci obdrží surrogated instance z tabulky objektu.  
  
 Předchozí příklad převede objekty typu `InventorySurrogated` zpět na počáteční typ `Inventory`. V takovém případě přímo přenosu dat zpět z `InventorySurrogated` jeho odpovídající pole v `Inventory`. Protože nejsou k dispozici žádné manipulace dat, každý člen pole bude obsahovat stejné hodnoty jako před serializaci.  
  
### <a name="getcustomdatatoexport-method"></a>GetCustomDataToExport – metoda  
 Při exportu schéma, <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A> metoda je volitelná. Umožňuje vložit další data nebo pomocné parametry do exportovaný schématu. Na úrovni typ nebo člen úrovně jde vložit další data. Příklad:  
  
 [!code-csharp[C_IDataContractSurrogate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#6)]  
  
 Tato metoda (se dvěma přetížení) umožňuje zahrnutí doplňující informace do metadat buď na úrovni člena nebo typu. Je možné zahrnout pomocné parametry o tom, zda člen veřejné nebo soukromé a komentáře, které by zachovaná v průběhu exportu a importu schématu. Tyto informace by dojít ke ztrátě bez této metody. Tato metoda nezpůsobí vložení nebo odstranění typů nebo členy, ale spíš přidá další data schémata na kteroukoli z těchto úrovní.  
  
 Metoda je přetížena a může trvat buď `Type` (`clrtype` parametr) nebo <xref:System.Reflection.MemberInfo> (`memberInfo` parametr). Druhý parametr je vždy `Type` (`dataContractType` parametr). Tato metoda je volána pro každý člen a typ surrogated `dataContractType` typu.  
  
 Některé z těchto přetížení musí vracet buď `null` nebo serializovatelný objekt. Poznámky na exportovaný schéma bude serializovat objekt nesmí být nulová. Pro `Type` přetížení, každý typ, který je exportován do schématu posílá tuto metodu v společně s surrogated typ jako první parametr `dataContractType` parametr. Pro `MemberInfo` přetížení, každý člen, který je exportován do schématu odešle její informace, jako `memberInfo` parametr s surrogated typu v druhý parametr.  
  
#### <a name="getcustomdatatoexport-method-type-type"></a>Metoda GetCustomDataToExport (typ, typ)  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Type%2CSystem.Type%29?displayProperty=nameWithType> Metoda je volána při exportu schématu pro každý typ definici. Při exportu metodu přidá informace do typů v rámci schématu. Každý typ definované posílá této metodě určit, jestli je žádná další data, která musí být součástí ve schématu.  
  
#### <a name="getcustomdatatoexport-method-memberinfo-type"></a>Metoda GetCustomDataToExport (MemberInfo –, typ).  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=nameWithType> Je volána v průběhu exportu pro každý člen v typy, které jsou exportovány. Tato funkce umožňuje přizpůsobit jakékoli komentáře pro členy, které budou zahrnuty ve schématu při exportu. Informace o všech členů v rámci třídy posílá této metody zkontrolujte, zda žádná další data je třeba přidat ve schématu.  
  
 V příkladu výše hledání prostřednictvím `dataContractType` pro každého člena náhradního. Pak vrátí modifikátor odpovídající přístup pro každé pole. Bez této přizpůsobení je výchozí hodnota pro modifikátory přístupu veřejné. Všichni členové proto by být definován jako veřejné v kód, který vygenerovala pomocí exportovaný schématu bez ohledu na to, jaké jsou jejich omezení skutečné přístupu. Pokud nepoužíváte Tato implementace člen `numpens` by být veřejné v exportovaném schématu, i když byl definován v náhradní jako privátní. Prostřednictvím této metody v exportovaném schématu mohou být generována – modifikátor přístupu jako soukromé.  
  
### <a name="getreferencedtypeonimport-method"></a>GetReferencedTypeOnImport – metoda  
 Tato metoda se mapuje <xref:System.Type> náhradního původní typu. Tato metoda je volitelné pro import schématu.  
  
 Při vytváření náhradní, který importuje schéma a vygeneruje pro ni kód, je dalším krokem k definování typu náhradní instance na původní.  
  
 Pokud generovaný kód musí odkazovat na existující typ uživatele, k tomu je potřeba implementace <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> metoda.  
  
 Při importu schéma, tato metoda je volána pro každý typ deklarace k mapování kontrakt surrogated dat na typ. Parametry řetězce `typeName` a `typeNamespace` zadat název a obor názvů surrogated typu. Návratovou hodnotu pro <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> slouží k určení, zda je třeba vytvořit nový typ. Tato metoda musí vrátit platný typ nebo hodnotu null. Typ vrácený se použije pro platné typy jako odkazovaný typ generovaného kódu. Pokud vrátí se hodnota null, se bude odkazovat žádný typ a nový typ musí být vytvořen. Pokud existuje několik náhrady, je možné provést pro každý typ náhradní zpět na typ počáteční mapování.  
  
 `customData` Parametr je objekt původně vrácený <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A>. To `customData` se používá při náhradní autoři chcete vložit další data nebo pomocné parametry do metadat, které mají být použita ke generování kódu.  
  
### <a name="processimportedtype-method"></a>ProcessImportedType – metoda  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.ProcessImportedType%2A> Metoda přizpůsobí jakýkoli typ vytvořené z import schématu. Tato metoda je volitelné.  
  
 Při importu schéma, tato metoda umožňuje pro importovaný typ a kompilace informace k přizpůsobení. Příklad:  
  
 [!code-csharp[C_IDataContractSurrogate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#7)]  
  
 Během importu tato metoda je volána pro každý typ vygenerovat. Změnit zadaný <xref:System.CodeDom.CodeTypeDeclaration> nebo upravit <xref:System.CodeDom.CodeCompileUnit>. To zahrnuje změnu názvu, členy, atributy a mnoho dalších vlastností `CodeTypeDeclaration`. Zpracováním `CodeCompileUnit`, je možné upravit direktivy, obory názvů, odkazovaná sestavení a několik dalších aspektů.  
  
 `CodeTypeDeclaration` Parametr obsahuje deklaraci typu DOM kódu. `CodeCompileUnit` Parametr umožňuje upravovat pro zpracování kód.  Vrácení `null` výsledkem deklarace typu, budou odstraněny. Naopak při vrácení `CodeTypeDeclaration`, změny se zachovají.  
  
 Při exportu metadat je vložit vlastní data, musí být uživateli poskytnutý při importu, aby ho bylo možné použít. Tato vlastní data lze pro programování pomocné parametry modelu nebo jiných komentáře. Každý `CodeTypeDeclaration` a <xref:System.CodeDom.CodeTypeMember> instance zahrnuje vlastní data jako <xref:System.CodeDom.CodeObject.UserData%2A> vlastnost přetypovat `IDataContractSurrogate` typu.  
  
 V předchozím příkladu provádí některé změny schématu naimportovány. Kód zachová soukromé členy původní typu pomocí náhradní. Výchozí modifikátor přístupu při importu schématu je `public`. Proto bude všichni členové náhradní schéma veřejné, pokud nezměnil, jako v následujícím příkladu. Během exportu vloží se do metadata o tom, které jsou členy soukromá vlastní data. V příkladu vlastní data pro vyhledávání, ověří, zda je privátní – modifikátor přístupu a pak upravením příslušného člena na privátní, a nastavení jeho atributy. Bez této přizpůsobení `numpens` člen je definován jako veřejné místo soukromé.  
  
### <a name="getknowncustomdatatypes-method"></a>GetKnownCustomDataTypes – metoda  
 Tato metoda získá z schéma definované vlastní datové typy. Metoda je volitelné pro import schématu.  
  
 Metoda je volána na začátku schématu exportu a importu. Metoda vrátí vlastní datové typy používá ve schématu exportovat nebo importovat. Byla předána metodě <xref:System.Collections.ObjectModel.Collection%601> ( `customDataTypes` parametr), což je kolekci typů. Metoda měli přidat další známé typy k této kolekci. Známé vlastní datové typy jsou potřebná k povolení serializace a deserializace pomocí vlastních dat <xref:System.Runtime.Serialization.DataContractSerializer>. Další informace najdete v tématu [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="implementing-a-surrogate"></a>Implementace náhradní  
 Pokud chcete použít náhradní kontraktu dat v rámci WCF, je třeba provést několik zvláštní postupy.  
  
### <a name="to-use-a-surrogate-for-serialization-and-deserialization"></a>Použít náhradní serializace a deserializace  
 Použití <xref:System.Runtime.Serialization.DataContractSerializer> k provedení serializace a deserializace dat pomocí náhradní. <xref:System.Runtime.Serialization.DataContractSerializer> Je vytvořené <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>. Musí být zadaná také náhradní.  
  
##### <a name="to-implement-serialization-and-deserialization"></a>K implementaci serializace a deserializace  
  
1.  Vytvoření instance <xref:System.ServiceModel.ServiceHost> pro vaši službu. Úplné pokyny naleznete v části [základní programování WCF](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
2.  Pro každý <xref:System.ServiceModel.Description.ServiceEndpoint> hostitele určenou službu najít jeho <xref:System.ServiceModel.Description.OperationDescription>.  
  
3.  Vyhledávání pomocí operace chování k určení, zda instanci <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> nalezen.  
  
4.  Pokud <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> je najít, nastavte jeho <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> vlastnost do nové instance náhradního. Pokud žádné <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> je najít, vytvořte novou instanci a nastavte <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> členem do nové instance náhradního nové chování.  
  
5.  Nakonec přidejte toto nové chování pro aktuální operaci chování, jak je znázorněno v následujícím příkladu:  
  
     [!code-csharp[C_IDataContractSurrogate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#8)]  
  
### <a name="to-use-a-surrogate-for-metadata-import"></a>Použít náhradní pro Import metadat  
 Při importu metadat jako WSDL a XSD ke generování kódu na straně klienta, musí být přidán do komponentu starost generování kódu z schématu XSD náhradní <xref:System.Runtime.Serialization.XsdDataContractImporter>. Chcete-li to provést přímo upravit <xref:System.ServiceModel.Description.WsdlImporter> používá pro import metadat.  
  
##### <a name="to-implement-a-surrogate-for-metadata-importation"></a>K implementaci náhradní pro import metadat  
  
1.  Import metadat pomocí <xref:System.ServiceModel.Description.WsdlImporter> třídy.  
  
2.  Použití <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metody zkontrolujte, zda <xref:System.Runtime.Serialization.XsdDataContractImporter> byla definována.  
  
3.  Pokud <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metoda vrátí `false`, vytvořte novou <xref:System.Runtime.Serialization.XsdDataContractImporter> a nastavit jeho <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> vlastnost novou instanci třídy <xref:System.Runtime.Serialization.ImportOptions> – třída. Jinak použijte – Importér vrácený `out` parametr <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metoda.  
  
4.  Pokud <xref:System.Runtime.Serialization.XsdDataContractImporter> neobsahuje žádné <xref:System.Runtime.Serialization.ImportOptions> definované, pak nastavte vlastnost, která má být novou instanci třídy <xref:System.Runtime.Serialization.ImportOptions> třídy.  
  
5.  Nastavte <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A> vlastnost <xref:System.Runtime.Serialization.ImportOptions> z <xref:System.Runtime.Serialization.XsdDataContractImporter> do nové instance náhradního.  
  
6.  Přidat <xref:System.Runtime.Serialization.XsdDataContractImporter> ke kolekci vrácené <xref:System.ServiceModel.Description.MetadataExporter.State%2A> vlastnost <xref:System.ServiceModel.Description.WsdlImporter> (zděděno z <xref:System.ServiceModel.Description.MetadataExporter> třídy.)  
  
7.  Použití <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> metodu <xref:System.ServiceModel.Description.WsdlImporter> pro import všech kontraktů dat ve schématu. Při posledním kroku z schémata načíst voláním náhradní generování kódu.  
  
     [!code-csharp[C_IDataContractSurrogate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#9)]  
  
### <a name="to-use-a-surrogate-for-metadata-export"></a>Chcete-li použít náhradní pro Export metadat  
 Ve výchozím nastavení, pokud Export metadat z WCF pro služby je třeba vytvořit WSDL i XSD schématu. Náhradní musí být přidán do komponentu starost generování schématu XSD pro typy kontraktů dat, <xref:System.Runtime.Serialization.XsdDataContractExporter>. K tomuto účelu použijte chování, který implementuje <xref:System.ServiceModel.Description.IWsdlExportExtension> změnit <xref:System.ServiceModel.Description.WsdlExporter>, nebo přímo upravit <xref:System.ServiceModel.Description.WsdlExporter> používá pro export metadat.  
  
##### <a name="to-use-a-surrogate-for-metadata-export"></a>Chcete-li použít náhradní pro export metadat  
  
1.  Vytvořte novou <xref:System.ServiceModel.Description.WsdlExporter> nebo použít `wsdlExporter` byl předán parametr <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> metoda.  
  
2.  Použití <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> funkce lze zjistit, jestli <xref:System.Runtime.Serialization.XsdDataContractExporter> byla definována.  
  
3.  Pokud <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> vrátí `false`, vytvořte novou <xref:System.Runtime.Serialization.XsdDataContractExporter> s generovaného schémat XML z <xref:System.ServiceModel.Description.WsdlExporter>a přidejte ji do kolekce vrácené <xref:System.ServiceModel.Description.MetadataExporter.State%2A> vlastnost <xref:System.ServiceModel.Description.WsdlExporter>. Jinak použijte exportu vrácený `out` parametr <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metoda.  
  
4.  Pokud <xref:System.Runtime.Serialization.XsdDataContractExporter> neobsahuje žádné <xref:System.Runtime.Serialization.ExportOptions> definované, pak nastavte <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> vlastnost novou instanci třídy <xref:System.Runtime.Serialization.ExportOptions> – třída.  
  
5.  Nastavte <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A> vlastnost <xref:System.Runtime.Serialization.ExportOptions> z <xref:System.Runtime.Serialization.XsdDataContractExporter> do nové instance náhradního. Následné kroky pro export metadat nevyžadují žádné změny.  
  
     [!code-csharp[C_IDataContractSurrogate#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#10)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.IDataContractSurrogate>  
 <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
 <xref:System.Runtime.Serialization.ImportOptions>  
 <xref:System.Runtime.Serialization.ExportOptions>  
 [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
