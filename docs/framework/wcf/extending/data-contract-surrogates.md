---
title: Náhrady kontraktů dat
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts [WCF], surrogates
ms.assetid: 8c31134c-46c5-4ed7-94af-bab0ac0dfce5
ms.openlocfilehash: cc0772cbb35f7c149af7eac04239d7349fa79f27
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797198"
---
# <a name="data-contract-surrogates"></a>Náhrady kontraktů dat
*Náhrada* kontraktu dat je pokročilou funkcí založenou na modelu kontraktu dat. Tato funkce je navržena pro použití pro vlastní nastavení a nahrazování typů v situacích, kdy uživatelé chtějí změnit způsob, jakým je typ serializovaný, deserializovaný nebo projektový do metadat. Některé scénáře, kde je možné použít náhradní údaje, jsou v případě, že se kontrakt dat pro typ nezadal, pole a vlastnosti nejsou označeny <xref:System.Runtime.Serialization.DataMemberAttribute> atributem nebo uživatelé, kteří chtějí dynamicky vytvářet variace schémat.  
  
 Serializace a deserializace se dokončí s náhradou kontraktu <xref:System.Runtime.Serialization.DataContractSerializer> dat při použití k převodu z .NET Framework do vhodného formátu, jako je například XML. Náhradu za kontrakt dat lze také použít ke změně metadat exportovaných pro typy při vytváření reprezentace metadat, jako jsou například dokumenty schématu XML (XSD). Při importu je kód vytvořen z metadat a v tomto případě lze použít náhradní číslo pro přizpůsobení vygenerovaného kódu.  
  
## <a name="how-the-surrogate-works"></a>Jak náhradní funguje  
 Náhradní funguje tak, že namapuje jeden typ ("původní" typ) na jiný typ ("typ" "" "". Následující příklad ukazuje původní typ `Inventory` a nový typ náhrady. `InventorySurrogated` Typ `Inventory` není serializovatelný, `InventorySurrogated` ale typ je:  
  
 [!code-csharp[C_IDataContractSurrogate#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#1)]  
  
 Vzhledem k tomu, že se kontrakt dat pro tuto třídu nedefinoval, převeďte třídu na náhradní třídu s kontraktem dat. V následujícím příkladu je uvedena třída s zástupnou třídou:  
  
 [!code-csharp[C_IDataContractSurrogate#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#2)]  
  
## <a name="implementing-the-idatacontractsurrogate"></a>Implementace rozhraní IDataContractSurrogate  
 Chcete-li použít náhradní smlouvu o data, <xref:System.Runtime.Serialization.IDataContractSurrogate> implementujte rozhraní.  
  
 Následuje přehled každé metody <xref:System.Runtime.Serialization.IDataContractSurrogate> s možnou implementací.  
  
### <a name="getdatacontracttype"></a>GetDataContractType  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Metoda mapuje jeden typ na jiný. Tato metoda je vyžadována pro serializaci, deserializaci, import a export.  
  
 První úkol definuje, které typy budou namapovány na jiné typy. Příklad:  
  
 [!code-csharp[C_IDataContractSurrogate#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#3)]  
  
- U serializace je mapování vrácené touto metodou následně použito k transformaci původní instance na náhradní instanci voláním <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> metody.  
  
- V případě deserializace je mapování vracené touto metodou použito serializátorem k deserializaci do instance náhradního typu. Následně volá <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> transformaci náhradní instance do instance původního typu.  
  
- Při exportu se typ náhrady vrácený touto metodou projeví pro získání kontraktu dat, který se má použít pro generování metadat.  
  
- Při importu se počáteční typ změní na typ náhrady, který se odráží k získání kontraktu dat, který se má použít pro účely, jako je například odkazování na podporu.  
  
 <xref:System.Type> Parametr je typ objektu, který je serializován, je deserializovaný, importovaný nebo exportovaný. <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Metoda musí vracet vstupní typ, pokud náhrada nezpracovává typ. Jinak vraťte odpovídající typ s náhradami. Pokud existuje několik náhradních typů, lze v této metodě definovat mnoho mapování.  
  
 Metoda není volána pro předdefinované primitivy kontraktu dat, <xref:System.Int32> například nebo <xref:System.String>. <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> Pro jiné typy, jako jsou pole, uživatelsky definované typy a další datové struktury, bude tato metoda volána pro každý typ.  
  
 V předchozím příkladu metoda kontroluje, zda je `type` parametr a `Inventory` srovnatelný. Pokud ano, metoda ho mapuje na `InventorySurrogated`. Při každém volání serializace, deserializace, import schématu nebo exportu schématu je tato funkce volána jako první, aby bylo zjištěno mapování mezi typy.  
  
### <a name="getobjecttoserialize-method"></a>Metoda GetObjectToSerialize  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> Metoda převede původní instanci typu na instanci náhradního typu. Metoda je vyžadována pro serializaci.  
  
 Dalším krokem je definovat způsob, jakým budou fyzická data namapována z původní instance na náhradu tím, že implementuje <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> metodu. Příklad:  
  
 [!code-csharp[C_IDataContractSurrogate#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#4)]  
  
 Metoda <xref:System.Runtime.Serialization.IDataContractSurrogate.GetObjectToSerialize%2A> je volána, když je objekt serializován. Tato metoda přenáší data z původního typu na pole v typu s náhradami. Pole mohou být přímo namapována na náhradní pole nebo manipulace s původními daty mohou být uloženy v náhradních. Mezi možná použití patří: přímo mapování polí, provádění operací s daty, která se mají Uložit do zástupných polí nebo ukládání XML původního typu do pole s příponou.  
  
 `targetType` Parametr odkazuje na deklarovaný typ člena. Tento parametr je nahrazený typ vrácený <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDataContractType%2A> metodou. Serializátor neuplatňuje, že vrácený objekt je možné přiřadit tomuto typu. `obj` Parametr je objekt, který se má serializovat, a v případě potřeby se převede na jeho náhradní hodnotu. Tato metoda musí vracet vstupní objekt, pokud ho zástupný objekt nezpracovává. V opačném případě bude vrácen nový objekt náhrady. Náhrada není volána, pokud je objekt null. V rámci této metody lze definovat řadu náhradních mapování pro různé instance.  
  
 Při vytváření <xref:System.Runtime.Serialization.DataContractSerializer>můžete dát pokyn, aby zachoval odkazy na objekty. (Další informace naleznete v tématu [serializace a deserializace](../feature-details/serialization-and-deserialization.md).) To se provádí nastavením `preserveObjectReferences` parametru v jeho konstruktoru na. `true` V takovém případě je náhrada pro objekt volána pouze jednou, protože všechny následné serializace pouze zapisují odkaz do datového proudu. Pokud `preserveObjectReferences` je nastaveno na `false`, pak je náhrada volána pokaždé, když dojde k výskytu instance.  
  
 Pokud se typ serializované instance liší od deklarovaného typu, informace o typu jsou zapsány do datového proudu, například, `xsi:type` aby bylo možné instanci deserializovat na druhém konci. K tomuto procesu dochází, pokud je objekt zástupný nebo nikoli.  
  
 Výše uvedený příklad převede data `Inventory` instance na. `InventorySurrogated` Kontroluje typ objektu a provádí nezbytné manipulace pro převod na typ s náhradami. V tomto případě jsou pole `Inventory` třídy přímo zkopírována `InventorySurrogated` do polí třídy.  
  
### <a name="getdeserializedobject-method"></a>Metoda GetDeserializedObject  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetDeserializedObject%2A> Metoda převede instanci náhradního typu na původní instanci typu. Vyžaduje se pro deserializaci.  
  
 Dalším úkolem je definovat způsob, jakým budou fyzická data z náhradní instance namapována na původní. Příklad:  
  
 [!code-csharp[C_IDataContractSurrogate#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#5)]  
  
 Tato metoda je volána pouze během deserializace objektu. Poskytuje mapování reverzních dat pro deserializaci z typu náhrady zpátky na původní typ. Podobně jako u metody můžou některé možné účely použít k přímé výměně dat polí, provádění operací s daty a ukládání dat XML. `GetObjectToSerialize` Při deserializaci nemusíte vždycky získávat přesné hodnoty dat z původní kvůli manipulaci v převodu dat.  
  
 `targetType` Parametr odkazuje na deklarovaný typ člena. Tento parametr je nahrazený typ vrácený `GetDataContractType` metodou. `obj` Parametr odkazuje na objekt, který byl deserializován. Objekt lze převést zpět na původní typ, pokud je náhradní. Tato metoda vrátí vstupní objekt, pokud náhrada nezpracovává objekt. V opačném případě se deserializovaný objekt vrátí po dokončení jeho převodu. Pokud existuje několik náhradních typů, můžete pro každý typ a převod zadat převod dat z náhradní na primární typ.  
  
 Při vrácení objektu se tabulky interních objektů aktualizují pomocí objektu vráceného touto náhradou. Jakékoli následné odkazy na instanci získají náhradní instanci z tabulek objektů.  
  
 Předchozí příklad převede objekty typu `InventorySurrogated` zpět na počáteční typ. `Inventory` V tomto případě se data přímo přenesou zpátky z `InventorySurrogated` do příslušných polí v. `Inventory` Vzhledem k tomu, že neexistují žádná manipulace s daty, budou každé pole členů obsahovat stejné hodnoty jako před serializací.  
  
### <a name="getcustomdatatoexport-method"></a>Metoda GetCustomDataToExport  
 Při exportu schématu <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A> je metoda volitelná. Slouží k vložení dalších dat nebo nápověd do exportovaného schématu. Další data lze vložit na úrovni člena nebo typu. Příklad:  
  
 [!code-csharp[C_IDataContractSurrogate#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#6)]  
  
 Tato metoda (se dvěma přetíženími) umožňuje zahrnutí dalších informací do metadat buď na úrovni člena, nebo typu. Je možné zahrnout nápovědu týkající se toho, zda je člen veřejný nebo privátní, a komentáře, které by byly zachovány během exportu a importu schématu. Tyto informace by byly ztraceny bez této metody. Tato metoda nezpůsobí vložení ani odstranění členů nebo typů, ale místo toho přidá další data do schémat na obou těchto úrovních.  
  
 Metoda je přetížena a může mít `Type` buď (`clrtype` parametr), nebo <xref:System.Reflection.MemberInfo> (`memberInfo` parametr). Druhý parametr je vždy typu `Type` (`dataContractType` parametr). Tato metoda je volána pro každý člen a typ náhradního `dataContractType` typu.  
  
 Jedno z těchto přetížení musí vracet buď `null` nebo serializovatelný objekt. Objekt, který nemá hodnotu null, bude serializován jako anotace do exportovaného schématu. Pro přetížení jsou všechny typy, které jsou exportovány do schématu, odesílány do této metody v prvním parametru spolu s nahrazeným typem `dataContractType` jako parametr. `Type` Pro přetížení odesílá každý člen, který je exportován do schématu, své informace `memberInfo` jako parametr s nahrazeným typem ve druhém parametru. `MemberInfo`  
  
#### <a name="getcustomdatatoexport-method-type-type"></a>GetCustomDataToExport – metoda (Type, Type)  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Type%2CSystem.Type%29?displayProperty=nameWithType> Metoda je volána během exportu schématu pro každou definici typu. Metoda přidává informace k typům v rámci schématu při exportu. Každý definovaný typ je odeslán této metodě k určení, zda existují další data, která je třeba zahrnout do schématu.  
  
#### <a name="getcustomdatatoexport-method-memberinfo-type"></a>GetCustomDataToExport – metoda (MemberInfo, Type)  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%28System.Reflection.MemberInfo%2CSystem.Type%29?displayProperty=nameWithType> Je volána během exportu pro každého člena v typech, které jsou exportovány. Tato funkce umožňuje přizpůsobit všechny komentáře pro členy, kteří budou součástí schématu při exportu. Informace pro každého člena v rámci třídy se odesílají této metodě, aby zkontrolovala, jestli je potřeba přidat do schématu nějaká další data.  
  
 Výše uvedený příklad vyhledává `dataContractType` pro každého člena náhrady. Pak vrátí odpovídající modifikátor přístupu pro každé pole. Bez tohoto vlastního nastavení je výchozí hodnota pro modifikátory přístupu veřejná. Proto budou všichni členové definováni jako veřejné v kódu generovaném pomocí exportovaného schématu bez ohledu na to, jaká jsou jejich skutečná omezení přístupu. Pokud tato implementace nepoužíváte, člen `numpens` by byl v exportovaném schématu veřejný i v případě, že byl definován v náhradní podobě jako soukromý. Pomocí této metody se v exportovaném schématu dá modifikátor přístupu vygenerovat jako soukromý.  
  
### <a name="getreferencedtypeonimport-method"></a>Metoda GetReferencedTypeOnImport  
 Tato metoda mapuje <xref:System.Type> náhradu na původní typ. Tato metoda je volitelná pro import schématu.  
  
 Při vytváření náhrady, která importuje schéma a generuje pro něj kód, je dalším úkolem definování typu náhradní instance na původním typu.  
  
 Pokud generovaný kód musí odkazovat na existující typ uživatele, je to provedeno implementací <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> metody.  
  
 Při importu schématu je tato metoda volána pro každou deklaraci typu k mapování kontraktu náhradních dat na typ. Parametry `typeName` řetězce a `typeNamespace` definujte název a obor názvů pro typ s příponou. Návratová hodnota pro <xref:System.Runtime.Serialization.IDataContractSurrogate.GetReferencedTypeOnImport%2A> slouží k určení, zda je třeba vygenerovat nový typ. Tato metoda musí vracet buď platný typ, nebo hodnotu null. Pro platné typy bude vrácený typ použit jako odkazovaný typ ve vygenerovaném kódu. Pokud je vrácena hodnota null, nebude odkazován žádný typ a je třeba vytvořit nový typ. Pokud existuje více náhradních, je možné provést mapování pro každý typ náhrady zpátky na jeho počáteční typ.  
  
 Parametr je objekt původně vrácen z <xref:System.Runtime.Serialization.IDataContractSurrogate.GetCustomDataToExport%2A>. `customData` Tato `customData` funkce se používá v případě, že náhradní Autoři chtějí do metadat použít další data nebo nápovědu, aby je mohl použít při importu k vygenerování kódu.  
  
### <a name="processimportedtype-method"></a>Metoda ProcessImportedType  
 <xref:System.Runtime.Serialization.IDataContractSurrogate.ProcessImportedType%2A> Metoda přizpůsobí libovolný typ vytvořený z části Import schématu. Tato metoda je volitelná.  
  
 Při importu schématu Tato metoda umožňuje přizpůsobení veškerého importovaného typu a informací o kompilaci. Příklad:  
  
 [!code-csharp[C_IDataContractSurrogate#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#7)]  
  
 Během importu je tato metoda volána pro každý generovaný typ. Změňte zadané <xref:System.CodeDom.CodeTypeDeclaration> nebo <xref:System.CodeDom.CodeCompileUnit>změňte. To zahrnuje změnu názvu, členů, atributů a mnoha dalších vlastností `CodeTypeDeclaration`. Zpracováním `CodeCompileUnit`je možné upravit direktivy, obory názvů, odkazovaná sestavení a několik dalších aspektů.  
  
 `CodeTypeDeclaration` Parametr obsahuje deklaraci typu DOM kódu. `CodeCompileUnit` Parametr umožňuje úpravy pro zpracování kódu.  Vrací `null` se výsledky v deklaraci typu, která se zahodí. Naopak při vrácení `CodeTypeDeclaration`změn se změny zachovají.  
  
 Pokud jsou během exportu metadat vložena vlastní data, je nutné ji uživateli poskytnout během importu, aby ji bylo možné použít. Tato vlastní data lze použít k programování tipů modelu nebo k jiným komentářům. Každá `CodeTypeDeclaration` instance <xref:System.CodeDom.CodeTypeMember> a obsahujevlastní`IDataContractSurrogate` data jako vlastnostpřetypovánínatyp.<xref:System.CodeDom.CodeObject.UserData%2A>  
  
 Výše uvedený příklad provede některé změny importovaného schématu. Kód zachovává soukromé členy původního typu pomocí náhrady. Výchozí modifikátor přístupu při importu schématu `public`. Proto budou všichni členové schématu nahrazení veřejné, pokud se nezmění, jako v tomto příkladu. Během exportu se vlastní data vloží do metadat, o kterých jsou členové privátní. V příkladu jsou vyhledána vlastní data, zkontroluje, zda je modifikátor přístupu soukromý, a pak upraví příslušný člen tak, aby byl privátní, nastavením jeho atributů. Bez tohoto přizpůsobení by byl `numpens` člen definován jako veřejný, nikoli jako soukromý.  
  
### <a name="getknowncustomdatatypes-method"></a>Metoda GetKnownCustomDataTypes  
 Tato metoda získá vlastní datové typy, které jsou definovány ve schématu. Metoda je volitelná pro import schématu.  
  
 Metoda je volána na začátku exportu schématu a importu. Metoda vrátí vlastní datové typy používané v exportovaném nebo importovaném schématu. Metoda je předána <xref:System.Collections.ObjectModel.Collection%601> `customDataTypes` (parametr), což je kolekce typů. Metoda by měla do této kolekce přidat další známé typy. Známé vlastní datové typy jsou potřebné k povolení serializace a deserializace vlastních dat pomocí <xref:System.Runtime.Serialization.DataContractSerializer>. Další informace najdete v tématu [známé typy kontraktů dat](../feature-details/data-contract-known-types.md).  
  
## <a name="implementing-a-surrogate"></a>Implementace náhrady  
 Chcete-li v rámci služby WCF použít náhradu za kontrakt dat, je nutné dodržovat několik zvláštních postupů.  
  
### <a name="to-use-a-surrogate-for-serialization-and-deserialization"></a>Použití náhradních pro serializaci a deserializaci  
 <xref:System.Runtime.Serialization.DataContractSerializer> Použijte k provedení serializace a deserializace dat s náhradou. <xref:System.Runtime.Serialization.DataContractSerializer> Je vytvořen <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>pomocí. Je také nutné zadat náhradní.  
  
##### <a name="to-implement-serialization-and-deserialization"></a>Implementace serializace a deserializace  
  
1. Vytvořte instanci <xref:System.ServiceModel.ServiceHost> služby pro vaši službu. Podrobné pokyny najdete v tématu [Základní programování WCF](../basic-wcf-programming.md).  
  
2. Pro každého <xref:System.ServiceModel.Description.ServiceEndpoint> zadaného hostitele služby Najděte jeho <xref:System.ServiceModel.Description.OperationDescription>.  
  
3. Pokud chcete zjistit, jestli se našla instance, <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> vyhledejte v chování operace.  
  
4. Pokud je nalezen, nastavte jeho <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> vlastnost na novou instanci náhrady. <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior> Pokud se nenajde, vytvořte novou instanci a <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.DataContractSurrogate%2A> nastavte člena nového chování na novou instanci náhrady. <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>  
  
5. Nakonec přidejte toto nové chování do chování aktuální operace, jak je znázorněno v následujícím příkladu:  
  
     [!code-csharp[C_IDataContractSurrogate#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#8)]  
  
### <a name="to-use-a-surrogate-for-metadata-import"></a>Použití náhrady při importu metadat  
 Při importu metadat, jako je WSDL a XSD, pro generování kódu na straně klienta, je nutné přidat náhradní komponentu do komponenty zodpovědné za generování kódu ze schématu <xref:System.Runtime.Serialization.XsdDataContractImporter>XSD. Provedete to tak, že <xref:System.ServiceModel.Description.WsdlImporter> přímo upravíte použití pro import metadat.  
  
##### <a name="to-implement-a-surrogate-for-metadata-importation"></a>Implementace náhrady při dovozu metadat  
  
1. Importujte metadata pomocí <xref:System.ServiceModel.Description.WsdlImporter> třídy.  
  
2. Použijte metodu ke kontrole, zda <xref:System.Runtime.Serialization.XsdDataContractImporter> byl definován. <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>  
  
3. `false` <xref:System.Runtime.Serialization.XsdDataContractImporter> Pokud metoda vrátí, vytvořte novou a nastavte <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> <xref:System.Runtime.Serialization.ImportOptions> její vlastnost na novou instanci třídy. <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> V opačném případě použijte import vrácený `out` parametrem <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metody.  
  
4. Pokud není definován, nastavte vlastnost tak, aby byla novou instancí <xref:System.Runtime.Serialization.ImportOptions> třídy. <xref:System.Runtime.Serialization.ImportOptions> <xref:System.Runtime.Serialization.XsdDataContractImporter>  
  
5. <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A> Nastavte vlastnost <xref:System.Runtime.Serialization.ImportOptions> pro nanovouinstancináhrady.<xref:System.Runtime.Serialization.XsdDataContractImporter>  
  
6. Přidejte do kolekce vrácené <xref:System.ServiceModel.Description.MetadataExporter.State%2A> vlastností <xref:System.ServiceModel.Description.WsdlImporter> (zděděné ze <xref:System.ServiceModel.Description.MetadataExporter> třídy). <xref:System.Runtime.Serialization.XsdDataContractImporter>  
  
7. <xref:System.ServiceModel.Description.WsdlImporter.ImportAllContracts%2A> Použijte metodu <xref:System.ServiceModel.Description.WsdlImporter> pro import všech kontraktů dat v rámci schématu. Během posledního kroku se kód generuje ze schémat načtených voláním do náhradní.  
  
     [!code-csharp[C_IDataContractSurrogate#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#9)]  
  
### <a name="to-use-a-surrogate-for-metadata-export"></a>Použití náhrady při exportu metadat  
 Ve výchozím nastavení je při exportu metadat z WCF pro službu nutné vygenerovat schéma WSDL i XSD. Náhradní je nutné přidat do komponenty zodpovědné za generování schématu XSD pro typy <xref:System.Runtime.Serialization.XsdDataContractExporter>kontraktů dat. K tomu použijte chování, které implementuje <xref:System.ServiceModel.Description.IWsdlExportExtension> k <xref:System.ServiceModel.Description.WsdlExporter>úpravě <xref:System.ServiceModel.Description.WsdlExporter> , nebo přímo upraví použití pro export metadat.  
  
##### <a name="to-use-a-surrogate-for-metadata-export"></a>Použití náhrady při exportu metadat  
  
1. Vytvořte nový <xref:System.ServiceModel.Description.WsdlExporter> nebo `wsdlExporter` použijte parametr předaný <xref:System.ServiceModel.Description.IWsdlExportExtension.ExportContract%2A> metodě.  
  
2. Pomocí funkce zkontrolujete, zda <xref:System.Runtime.Serialization.XsdDataContractExporter> byl definován. <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A>  
  
3. Pokud <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> se `false`vrátí, vytvořte nový <xref:System.Runtime.Serialization.XsdDataContractExporter> s generovanými schématy XML z <xref:System.ServiceModel.Description.WsdlExporter>a a <xref:System.ServiceModel.Description.WsdlExporter>přidejte je do kolekce vrácené <xref:System.ServiceModel.Description.MetadataExporter.State%2A> vlastností. V opačném případě použijte vývozce vrácený `out` parametrem <xref:System.Collections.Generic.Dictionary%602.TryGetValue%2A> metody.  
  
4. Pokud není definován,<xref:System.Runtime.Serialization.ExportOptions> nastavte vlastnost na novou instanci třídy. <xref:System.Runtime.Serialization.XsdDataContractExporter.Options%2A> <xref:System.Runtime.Serialization.ExportOptions> <xref:System.Runtime.Serialization.XsdDataContractExporter>  
  
5. <xref:System.Runtime.Serialization.ExportOptions.DataContractSurrogate%2A> Nastavte vlastnost <xref:System.Runtime.Serialization.ExportOptions> pro nanovouinstancináhrady.<xref:System.Runtime.Serialization.XsdDataContractExporter> Následující kroky pro export metadat nevyžadují žádné změny.  
  
     [!code-csharp[C_IDataContractSurrogate#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_idatacontractsurrogate/cs/source.cs#10)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.IDataContractSurrogate>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior>
- <xref:System.Runtime.Serialization.ImportOptions>
- <xref:System.Runtime.Serialization.ExportOptions>
- [Použití kontraktů dat](../feature-details/using-data-contracts.md)
