---
title: Náhrady kontraktů dat
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], surrogates
ms.assetid: 8c31134c-46c5-4ed7-94af-bab0ac0dfce5
ms.openlocfilehash: 7b1e8585755bbbff900bd621d8bc3a25fd23961c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64587508"
---
# <a name="data-contract-surrogates"></a>Náhrady kontraktů dat
Kontrakt dat *náhradní* je pokročilá funkce postavené na kontraktu dat modelu. Tato funkce je určena pro použití pro nahrazení v situacích, ve kterém chcete změnit, jak je typ serializován, deserializované nebo předpokládaných do metadat uživatelů a přizpůsobení typu. Při některých scénářích, kde mohou být použity náhradní kontraktu dat. není určeno pro typ, polí a vlastností nejsou označené <xref:System.Runtime.Serialization.DataMemberAttribute> atribut nebo uživatelům, aby dynamicky se vytvářejí odchylky schématu.  
  
 Serializace a deserializace jsou možné díky náhrada kontraktu dat při použití <xref:System.Runtime.Serialization.DataContractSerializer> pro převod z rozhraní .NET Framework na vhodném formátu, jako je například XML. Náhrada kontraktu dat lze také upravit metadata export pro typy, při vytváření metadat reprezentace například dokumentů schématu XML (XSD). Při importu kód je vytvořen z metadat a zástupný lze použít v tomto případě k přizpůsobení generovaný kód.  
  
## <a name="how-the-surrogate-works"></a>Jak funguje náhradní  
 Náhradní funguje tak, že mapování jednoho typu (typ "původní") k jinému typu (typ "surrogated"). Následující příklad ukazuje původní typ `Inventory` a nové náhradní `InventorySurrogated` typu. `Inventory` Typ není serializovatelný ale `InventorySurrogated` typ je:  
  
 [!code-csharp[C_IDataContractSurrogate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#1)]  
  
 Protože kontrakt dat nebyla definována pro tuto třídu, převeďte na náhradní třídy s kontraktem dat třídy. Surrogated třídy můžete vidět v následujícím příkladu:  
  
 [!code-csharp[C_IDataContractSurrogate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#2)]  
  
## <a name="implementing-the-idatacontractsurrogate"></a>Implementace IDataContractSurrogate  
 Použití náhrady kontraktů dat implementují <xref:System.Runtime.Serialization.IDataContractSurrogate> rozhraní.  
  
 Tady je přehled jednotlivých metod <xref:System.Runtime.Serialization.IDataContractSurrogate> s možnou implementaci.  
  
### <a name="getdatacontracttype"></a>GetDataContractType  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Metoda mapuje jednoho typu na jiný. Tato metoda je vyžadován pro serializaci, deserializace, import a export.  
  
 První úloha definuje, jaké typy budou mapována na jiné typy. Příklad:  
  
 [!code-csharp[C_IDataContractSurrogate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#3)]  
  
- Na serializaci, mapování vrácený touto metodou následně slouží k transformaci na původní instanci surrogated instanci voláním <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> metody.  
  
- K deserializaci používá mapování vrácený touto metodou serializátoru, který je k deserializaci do instance typu nahrazení. Následně volá <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> pro transformaci surrogated instance do instance původního typu.  
  
- Při exportu se projeví náhradní typ vrácený touto metodou zobrazíte kontraktu dat sloužící ke generování metadat.  
  
- Při importu změní se počáteční typ náhradní typ, který se projeví zobrazíte kontraktu dat pro účely jako odkazující na podporu.  
  
 <xref:System.Type> Je parametr typu objektu, která je serializována, deserializované, importované nebo exportovaná. <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Metoda musí vracet typ vstupu, pokud náhradní nezpracovává typ. V opačném případě vrátí surrogated příslušného typu. Pokud existuje několik typů náhradní mnoho mapování lze definovat v této metodě.  
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Metoda není volána pro předdefinované datové primitivy smlouvy, jako například <xref:System.Int32> nebo <xref:System.String>. U jiných typů, jako je například pole, uživatelem definované typy a další datové struktury bude tato metoda volána pro každý typ.  
  
 V předchozím příkladu metoda ověří, zda `type` parametr a `Inventory` lze porovnávat. Pokud ano, metoda mapuje na `InventorySurrogated`. Pokaždé, když serializace, se nazývá deserializace, schématu import nebo export schématu, tato funkce je volána nejprve určit mapování mezi typy.  
  
### <a name="getobjecttoserialize-method"></a>GetObjectToSerialize – metoda  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> Metoda převede na původní instanci typu surrogated typu instance. Metoda se vyžaduje pro serializaci.  
  
 Dalším krokem je určit způsob, jakým fyzické data budou zmapována z původní instance na zástupný implementací <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> metody. Příklad:  
  
 [!code-csharp[C_IDataContractSurrogate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#4)]  
  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> Metoda se volá, když je objekt serializován. Tato metoda přenosu dat z původního typu pole surrogated typu. Pole může být přímo mapována na náhradní pole nebo manipulaci s původní data mohou být uloženy v zástupný. Mezi možné použití patří: přímého mapování polí, provádění operací na data, která mají být uloženy v polích surrogated nebo uložení XML kódu původního typu surrogated pole.  
  
 `targetType` Parametr odkazuje na deklarovaný typ člena. Tento parametr je surrogated typ vrácený <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> metody. Serializátor nevynucuje, že se objekt vrácený přiřadit k tomuto typu. `obj` Parametru je objekt určený k serializaci, se převedou na jeho náhrada v případě potřeby. Tato metoda musí vracet vstupního objektu, pokud surrogated nezpracovává objektu. V opačném případě vrátí nový objekt náhrady. Zástupný není volána, pokud objekt má hodnotu null. Mnoho náhradní mapování pro různé instance může být definovaná v rámci této metody.  
  
 Při vytváření <xref:System.Runtime.Serialization.DataContractSerializer>, které dostane pokyn, aby zachovat odkazy na objekty. (Další informace najdete v tématu [serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).) To se provádí tak, že nastavíte `preserveObjectReferences` parametr v konstruktoru pro `true`. V takovém případě zástupný je volána pouze jednou pro objekt vzhledem k tomu, že všechny následné serializations stačí napsat odkaz do datového proudu. Pokud `preserveObjectReferences` je nastavena na `false`, pak náhradní je volána pokaždé, když je zjištěna instance.  
  
 Pokud typ instance serializovat se liší od deklarovaného typu, informace o typu například zapsána do datového proudu, `xsi:type` umožňující instance k deserializaci na druhém konci. Tento proces se provádí, zda je objekt surrogated nebo ne.  
  
 Výše uvedený příklad převede data `Inventory` instance u `InventorySurrogated`. Kontroluje, typu objektu a provede nezbytné manipulace převést na typ surrogated. V tomto případě pole `Inventory` třídy se přímo překopírují `InventorySurrogated` třídy pole.  
  
### <a name="getdeserializedobject-method"></a>GetDeserializedObject – metoda  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> Metoda převede surrogated typu instance na původní instanci typu. Je vyžadován pro deserializaci.  
  
 Dalším krokem je definování stejným způsobem jako fyzickou data budou zmapována z instance náhradní do původního. Příklad:  
  
 [!code-csharp[C_IDataContractSurrogate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#5)]  
  
 Tato metoda je volána pouze při deserializaci objektu. Poskytuje data reverzní mapování pro deserializace z typu náhradní zpět do původního stavu. Podobně jako `GetObjectToSerialize` metody, některé možné způsoby využití může být přímo výměnu dat pole, provést operace s daty a ukládání dat XML. Při deserializaci, nemusí vždy získat přesné datových hodnot z původní kvůli manipulace dat převodu.  
  
 `targetType` Parametr odkazuje na deklarovaný typ člena. Tento parametr je surrogated typ vrácený `GetDataContractType` metody. `obj` Parametr odkazuje na objekt, který má byla deserializovat. Objekt lze převést zpět na původní typ, pokud je surrogated. Tato metoda vrátí vstupní objekt, pokud zástupný objekt nezpracovává. Deserializovaný objekt, jinak bude vrácen, až se dokončí jeho převodu. Pokud existuje několik typů náhradní může poskytnout převod dat z náhradní na primární pro každou tak, že každý typ a jeho převodu.  
  
 Při vrácení objektu, interní objekt tabulky aktualizovány o objekt vrácený rutinou tato náhradní. Všechny následné odkazy na instanci získá surrogated instanci z tabulky objektů.  
  
 Předchozí příklad převede objekty typu `InventorySurrogated` zpět na původní typ `Inventory`. V takovém případě je přímo přenesená data zpět z `InventorySurrogated` na jeho odpovídající pole v `Inventory`. Vzhledem k tomu, že neexistují žádné manipulace dat, každý z pole člena, která bude obsahovat stejné hodnoty jako před serializace.  
  
### <a name="getcustomdatatoexport-method"></a>GetCustomDataToExport – metoda  
 Při exportu schématu, <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A> metoda je volitelná. Používá se k vložení dalších dat nebo parametrů do exportovaného schématu. Další data lze vložit na úrovni člena nebo na úrovni typu. Příklad:  
  
 [!code-csharp[C_IDataContractSurrogate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#6)]  
  
 Tato metoda (s dvě přetížení) umožňuje zařazení dodatečné informace do metadat na úrovni členů a typů. Je možné zahrnout nápovědu, zda je členem veřejné nebo privátní a komentáře, které by být zachována v rámci exportu a importu schématu. Tyto informace by dojít ke ztrátě bez této metody. Tato metoda nezpůsobí vložení nebo odstranění členy a typy, ale místo toho přidá další data schémata na některý z těchto úrovní.  
  
 Metoda je přetížena a můžete provést buď `Type` (`clrtype` parametr) nebo <xref:System.Reflection.MemberInfo> (`memberInfo` parametr). Druhý parametr je vždy `Type` (`dataContractType` parametr). Tato metoda je volána pro každý člen a typ surrogated `dataContractType` typu.  
  
 Některé z těchto přetížení musí vrátit buď `null` nebo serializovatelný objekt. Nenulový objekt bude serializována jako poznámky do exportovaného schématu. Pro `Type` přetížení, každý typ, který je exportován do schématu se odešle v společně s surrogated typ jako první parametr této metody `dataContractType` parametru. Pro `MemberInfo` přetížení každého člena, který je exportován do schématu odešle jako `memberInfo` parametr s typem surrogated ve druhém parametru.  
  
#### <a name="getcustomdatatoexport-method-type-type"></a>Metoda GetCustomDataToExport (typ, typ)  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Type%2CSystem.Type%29?displayProperty=nameWithType> Metoda je volána při exportu schématu pro každou definici typu. Metoda přidá informace do typů v rámci schématu při exportu. Každý definovaný typ posílá do této metody Určuje, jestli je dalších dat, který musí být součástí schématu.  
  
#### <a name="getcustomdatatoexport-method-memberinfo-type"></a>Metoda GetCustomDataToExport (MemberInfo, typ)  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=nameWithType> Je volána při exportu pro každého člena v typech, které jsou exportovány. Tato funkce umožňuje přizpůsobit žádné komentáře pro členy, které budou zahrnuty ve schématu při exportu. Informace pro každého člena v rámci třídy odesílat do této metody zkontrolujte, jestli žádná další data je potřeba přidat ve schématu.  
  
 V příkladu výše hledá v rámci `dataContractType` pro každého člena náhradního. Pak vrátí odpovídající přístup Modifikátor pro každé pole. Bez úprav výchozí hodnota pro modifikátory přístupu je veřejná. Proto všechny členy je definován jako veřejné v kódu generovaném, pomocí exportovaného schématu bez ohledu na to, jaké jsou jejich omezení skutečné přístupu. Pokud nepoužíváte implementovaný člen `numpens` by být veřejné ve schématu exportované i v případě, že byl definován v náhradní jako soukromá. Pomocí této metody v exportované schématu mohou být generovány modifikátor přístupu jako soukromé.  
  
### <a name="getreferencedtypeonimport-method"></a>GetReferencedTypeOnImport – metoda  
 Tato metoda se mapuje <xref:System.Type> náhradního k původnímu typu. Tato metoda je nepovinné pro import schématu.  
  
 Při vytváření náhradní, který importuje schéma a vygeneruje pro ni kód, dalším krokem je definování typu instance náhradní do původního stavu.  
  
 Pokud generovaný kód potřebuje k odkazování typu existujícího uživatele, je to provádí implementace <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> metody.  
  
 Když importujete schéma, tato metoda je volána pro každý typ deklarace k mapování kontraktu surrogated dat na typ. Parametry řetězce `typeName` a `typeNamespace` zadat název a obor názvů surrogated typu. Návratová hodnota pro <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> slouží k určení, jestli je potřeba vygenerovat nový typ. Tato metoda musí vrátit platný typ či null. Typ vrácený se použije pro platné typy jako odkazovaný typ v generovaném kódu. Pokud je vrácena hodnota null, bude odkazovat žádný typ a nový typ musí být vytvořen. Pokud existuje několik náhrady je možné provést mapování pro každý typ náhradní zpět na jeho původní typu.  
  
 `customData` Parametru je objekt původně vrácený <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A>. To `customData` se používá, když chcete vložit další data/pomocné parametry do metadat, která chcete použít ke generování kódu při importu náhradní autoři.  
  
### <a name="processimportedtype-method"></a>ProcessImportedType – metoda  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.ProcessImportedType%2A> Metoda přizpůsobuje libovolný typ vytvořený z import schématu. Tato metoda je volitelné.  
  
 Když importujete schéma, tato metoda umožňuje importovaný typ a kompilace informace k přizpůsobení. Příklad:  
  
 [!code-csharp[C_IDataContractSurrogate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#7)]  
  
 Při importu tato metoda je volána pro každý typ vygeneruje. Změnit zadanou <xref:System.CodeDom.CodeTypeDeclaration> nebo změnit <xref:System.CodeDom.CodeCompileUnit>. Jedná se o změnu názvu, členy, atributy a mnoho dalších vlastností `CodeTypeDeclaration`. Zpracováním `CodeCompileUnit`, je možné změnit direktivy, obory názvů, odkazovaná sestavení a několik jiných aspektů.  
  
 `CodeTypeDeclaration` Parametr obsahuje deklaraci typu modelu DOM kódu. `CodeCompileUnit` Parametr povoluje pro úpravy pro zpracování kódu.  Vrací `null` výsledků v deklaraci typu bude zahozen. Naopak při návratu `CodeTypeDeclaration`, změny jsou zachovány.  
  
 Pokud během exportu metadat vložení vlastních dat, musí to být uživateli poskytnutý při importu tak, že je možné. Tato vlastní data lze použít pro programovací model tipů nebo jiné poznámky. Každý `CodeTypeDeclaration` a <xref:System.CodeDom.CodeTypeMember> instance obsahuje vlastní data, jako <xref:System.CodeDom.CodeObject.UserData%2A> převedená na `IDataContractSurrogate` typu.  
  
 Výše uvedený příklad provede několik změn schématu importovat. Kód zachová pomocí náhradní soukromé členy původního typu. Výchozí modifikátor přístupu při importu schématu `public`. Všichni členové schématu náhradní proto bude veřejné, pokud se změní, jako v následujícím příkladu. Během exportu vložení vlastních dat do metadata o tom, které jsou privátní členy. Tento příklad vyhledá vlastní data, zkontroluje, jestli je privátní modifikátor přístupu a pak změní příslušného člena na privátní nastavením jeho atributy. Bez úprav `numpens` člen je definován jako veřejné místo privátní.  
  
### <a name="getknowncustomdatatypes-method"></a>GetKnownCustomDataTypes – metoda  
 Tato metoda získá vlastní datové typy, které jsou definované ve schématu. Metoda je nepovinné pro import schématu.  
  
 Metoda je volána na začátku schématu exportu a importu. Metoda vrací vlastní datové typy používané ve schématu exportovat nebo importovat. Metodě je předána <xref:System.Collections.ObjectModel.Collection%601> ( `customDataTypes` parametr), což je kolekce typů. Metoda by měla do této kolekce přidat další známé typy. Známý vlastní datové typy, které jsou potřebná k povolení serializace a deserializace pomocí vlastních dat <xref:System.Runtime.Serialization.DataContractSerializer>. Další informace najdete v tématu [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
## <a name="implementing-a-surrogate"></a>Implementace náhradní  
 Použití náhrada kontraktu dat v rámci WCF, je třeba dodržovat zvláštní jen pár postupů.  
  
### <a name="to-use-a-surrogate-for-serialization-and-deserialization"></a>Použít náhradní k serializaci a deserializaci  
 Použití <xref:System.Runtime.Serialization.DataContractSerializer> provést serializace a deserializace dat pomocí zástupný. <xref:System.Runtime.Serialization.DataContractSerializer> Vytvoří <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>. Musíte také zadat zástupný.  
  
##### <a name="to-implement-serialization-and-deserialization"></a>K implementaci serializace a deserializace  
  
1. Vytvoření instance <xref:System.ServiceModel.ServiceHost> pro vaši službu. Úplné pokyny najdete v tématu [základní programování WCF](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
2. Pro každý <xref:System.ServiceModel.Description.ServiceEndpoint> hostitele zadanou službu najít jeho <xref:System.ServiceModel.Description.OperationDescription>.  
  
3. Vyhledávání, po operaci chování k určení, zda instance <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> nenajde.  
  
4. Pokud <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> nalezen, nastavte jeho <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> vlastnost do nové instance náhradního. Pokud ne <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> je najít, vytvořte novou instanci a nastavte <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> členem nové chování náhradního do nové instance.  
  
5. Nakonec přidejte toto nové chování pro aktuální operaci chování, jak je znázorněno v následujícím příkladu:  
  
     [!code-csharp[C_IDataContractSurrogate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#8)]  
  
### <a name="to-use-a-surrogate-for-metadata-import"></a>Použít náhradní pro Import metadat  
 Při importu metadat, jako je WSDL nebo XSD pro generování kódu na straně klienta, musí být přidán do součást zodpovědná za generování kódu ze schématu XSD zástupný <xref:System.Runtime.Serialization.XsdDataContractImporter>. Chcete-li to provést přímo upravit <xref:System.ServiceModel.Description.WsdlImporter> používá pro import metadat.  
  
##### <a name="to-implement-a-surrogate-for-metadata-importation"></a>K implementaci náhradní pro import metadat  
  
1. Import metadat prostřednictvím <xref:System.ServiceModel.Description.WsdlImporter> třídy.  
  
2. Použití <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metodu ke kontrole, jestli <xref:System.Runtime.Serialization.XsdDataContractImporter> byla definována.  
  
3. Pokud <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> vrátí metoda `false`, vytvořte nový <xref:System.Runtime.Serialization.XsdDataContractImporter> a nastavte jeho <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> vlastností nové instance <xref:System.Runtime.Serialization.ImportOptions> třídy. Jinak použijte Importér vrácené `out` parametr <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metoda.  
  
4. Pokud <xref:System.Runtime.Serialization.XsdDataContractImporter> nemá žádné <xref:System.Runtime.Serialization.ImportOptions> definována, a nastavte vlastnost, která má být novou instanci třídy <xref:System.Runtime.Serialization.ImportOptions> třídy.  
  
5. Nastavte <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A> vlastnost <xref:System.Runtime.Serialization.ImportOptions> z <xref:System.Runtime.Serialization.XsdDataContractImporter> do nové instance náhradního.  
  
6. Přidat <xref:System.Runtime.Serialization.XsdDataContractImporter> na kolekci vrácené poskytovatelem <xref:System.ServiceModel.Description.MetadataExporter.State%2A> vlastnost <xref:System.ServiceModel.Description.WsdlImporter> (zděděno z <xref:System.ServiceModel.Description.MetadataExporter> třídy.)  
  
7. Použití <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> metodu <xref:System.ServiceModel.Description.WsdlImporter> pro import všech kontraktů dat v rámci schématu. Během poslední krok bude ze schémat načten voláním zástupný vygenerován kód.  
  
     [!code-csharp[C_IDataContractSurrogate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#9)]  
  
### <a name="to-use-a-surrogate-for-metadata-export"></a>Použít náhradní pro Export metadat  
 Ve výchozím nastavení při exportu metadat z WCF pro službu je potřeba vygenerovat schéma WSDL a XSD. Zástupný musí být přidán do součást zodpovědná za generování schématu XSD pro typy kontraktů dat, <xref:System.Runtime.Serialization.XsdDataContractExporter>. K tomuto účelu použijte chování, které implementuje <xref:System.ServiceModel.Description.IWsdlExportExtension> upravit <xref:System.ServiceModel.Description.WsdlExporter>, nebo přímo upravit <xref:System.ServiceModel.Description.WsdlExporter> použité pro export metadat.  
  
##### <a name="to-use-a-surrogate-for-metadata-export"></a>Použít náhradní pro export metadat  
  
1. Vytvořte nový <xref:System.ServiceModel.Description.WsdlExporter> nebo použijte `wsdlExporter` byl předán parametr <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> metody.  
  
2. Použití <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> funkce ke kontrole, jestli <xref:System.Runtime.Serialization.XsdDataContractExporter> byla definována.  
  
3. Pokud <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> vrátí `false`, vytvořte nový <xref:System.Runtime.Serialization.XsdDataContractExporter> generované schémata XML z <xref:System.ServiceModel.Description.WsdlExporter>a přidejte ho do kolekci vrácené poskytovatelem <xref:System.ServiceModel.Description.MetadataExporter.State%2A> vlastnost <xref:System.ServiceModel.Description.WsdlExporter>. Jinak použijte Exportér vrácené `out` parametr <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metody.  
  
4. Pokud <xref:System.Runtime.Serialization.XsdDataContractExporter> nemá žádné <xref:System.Runtime.Serialization.ExportOptions> definované, pak nastavte <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> vlastností nové instance <xref:System.Runtime.Serialization.ExportOptions> třídy.  
  
5. Nastavte <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A> vlastnost <xref:System.Runtime.Serialization.ExportOptions> z <xref:System.Runtime.Serialization.XsdDataContractExporter> do nové instance náhradního. Následné kroky pro export metadat nevyžadují žádné změny.  
  
     [!code-csharp[C_IDataContractSurrogate#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#10)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.IDataContractSurrogate>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.Runtime.Serialization.ImportOptions>
- <xref:System.Runtime.Serialization.ExportOptions>
- [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
