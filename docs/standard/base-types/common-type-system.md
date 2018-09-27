---
title: Obecný systém typů
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- type system
- common type system
- assemblies [.NET Framework], types
- reference types
- value types
- cross-language interoperability
- namespaces [.NET Framework], types
- types, about types
ms.assetid: 53c57c96-83e1-4ee3-9543-9ac832671a89
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c8db725e25fe441c875a25cba97eb2090d4c071
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47204199"
---
# <a name="common-type-system"></a>Obecný systém typů
Obecný systém typů definuje, jak jsou typy deklarovány, použití a spravovány v modulu common language runtime a také je důležitou součástí modulu runtime podpory mezi jazykové integrace. Obecný systém typů provádí následující funkce:  
  
-   Vytváří rámec, který pomáhá povolit mezi jazykové integrace, bezpečnost typů a spouštění vysoce výkonných kódu.  
  
-   Poskytuje objektově orientovaný model, který podporuje úplnou implementaci mnoha programovacích jazyků.  
  
-   Definuje pravidla, která musí jazyky, které pomáhá tak zajistit, že objekty, které jsou napsány v různých jazycích komunikovat mezi sebou.  
  
-   Poskytuje knihovnu obsahující primitivní datové typy (například <xref:System.Boolean>, <xref:System.Byte>, <xref:System.Char>, <xref:System.Int32>, a <xref:System.UInt64>) používané při vývoji aplikace.  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Typy v rozhraní .NET](#types_in_the_net_framework)  
  
-   [Definice typů](#type_definitions)  
  
-   [Členy typu](#type_members)  
  
-   [Charakteristiky členů typu](#characteristics_of_type_members)  
  
<a name="types_in_the_net_framework"></a>   
## <a name="types-in-net"></a>Typy v rozhraní .NET  
 Všechny typy v rozhraní .NET jsou buď hodnotové nebo odkazové typy.  
  
 Typy hodnot jsou datové typy, jejichž objekty jsou reprezentovány skutečnou hodnotou daného objektu. Pokud je instance hodnotového typu přiřazena proměnné, je této proměnné předána nová kopie hodnoty.  
  
 Odkazové typy jsou datové typy, jejichž objekty jsou reprezentovány s odkazem (podobným ukazateli) na skutečnou hodnotu objektu. Pokud je odkazový typ přiřazen k proměnné, tak tato proměnná odkazuje (směřuje) na původní hodnotu. Není vytvořena žádná kopie.  
  
 Obecný systém typů v rozhraní .NET podporuje následujících pět kategorií typů:  
  
-   [Třídy](#Classes)  
  
-   [Struktury](#Structures)  
  
-   [Výčty](#Enumerations)  
  
-   [Rozhraní](#Interfaces)  
  
-   [Delegáti](#Delegates)  
  
<a name="Classes"></a>   
### <a name="classes"></a>Třídy  
 Třída je typem odkazu, který může být odvozena přímo z jiné třídy a, který je implicitně odvozena z <xref:System.Object?displayProperty=nameWithType>. Třída definuje operace, může objekt (což je instance třídy) provádět (metody, události nebo vlastnosti) a data, že objekt obsahuje (položky). Přestože třída obecně zahrnuje definici i implementaci (na rozdíl od rozhraní, které obsahují pouze definici bez implementace), může mít jednoho nebo více členů, kteří implementaci nemají.  
  
 Následující tabulka popisuje některé vlastnosti, které třída může mít. Každý jazyk, který podporuje modul runtime poskytuje způsob, jak určit, který třídu nebo člen třídy má jednu nebo více těchto vlastností. Ale jednotlivé programovací jazyky, které cílí na .NET nemusí mít všechny tyto vlastnosti k dispozici.  
  
|Vlastnost|Popis|  
|--------------------|-----------------|  
|sealed|Určuje, že tento typ nelze odvodit jiné třídy.|  
|implements|Označuje, že třída používá jedno nebo více rozhraní, jelikož implementuje členy daného rozhraní.|  
|abstract|Označuje, že nelze vytvořit instanci třídy. Jeho použití, musí být odvozen jiné třídy z něj.|  
|Dědí|Označuje, že instance třídy lze použít všude, kde je zadán základní třídy. Odvozené třídy, která dědí ze základní třídy, můžete použít implementaci libovolného veřejného člena poskytuje základní třídu nebo odvozená třída může přepsat implementaci veřejného člena vlastní implementací.|  
|exportované nebo Neexportované|Určuje, zda je třída viditelná vně sestavení, ve kterém je definována. Tato vlastnost se týká pouze tříd na nejvyšší úrovni a vnořené třídy.|  
  
> [!NOTE]
>  Třída také může být vnořena v rodičovské třídě nebo struktuře. Vnořené třídy také mají členské charakteristiky. Další informace najdete v tématu [vnořené typy](#NestedTypes).  
  
 Členy třídy, které nemají implementaci se nazývají abstraktní členy. Třída, která má jeden nebo více abstraktních členů je sama o sobě abstraktní; Nelze vytvořit nové instance. Některé jazyky, které se zaměřují na modul runtime umožňují označit třídu jako abstraktní i v případě, že žádný z jejích členů není abstraktní. Můžete použít abstraktní třídu, pokud chcete zapouzdřit základní sadu funkcí, kterou odvozené třídy mohou dědit nebo v případě potřeby přepsat. Třídy, které nejsou abstraktní jsou označovány jako konkrétní třídy.  
  
 Třída může implementovat libovolný počet rozhraní, ale může dědit pouze z jediné základní třídy kromě <xref:System.Object?displayProperty=nameWithType>, z všechny třídy dědí implicitně. Všechny třídy musí mít alespoň jeden konstruktor, který inicializuje nové instance třídy. Pokud konstruktor explicitně nedefinujete, většina kompilátorů automaticky poskytne výchozí konstruktor (bez parametrů).  
  
<a name="Structures"></a>   
### <a name="structures"></a>Struktury  
 Struktura je hodnotový typ, který je implicitně odvozena z <xref:System.ValueType?displayProperty=nameWithType>, který je zase odvozen z <xref:System.Object?displayProperty=nameWithType>. Struktura je velmi užitečná pro reprezentování hodnot, jejichž požadavky na paměť jsou malé a pro předávání parametrů hodnotou metodám, které mají typově silné parametry. V rozhraní .NET, všechny primitivní datové typy (<xref:System.Boolean>, <xref:System.Byte>, <xref:System.Char>, <xref:System.DateTime>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.UInt16>, <xref:System.UInt32>, a <xref:System.UInt64>) jsou definovány jako struktury.  
  
 Stejně jako třídy struktury definují data (položky struktury) i operace, které lze provést na těchto datech (metody struktury). To znamená, že může volat metody ve strukturách včetně virtuálních metod definovaných v <xref:System.Object?displayProperty=nameWithType> a <xref:System.ValueType?displayProperty=nameWithType> třídy a jakékoli metody definované na samotném hodnotovém typu. Jinak řečeno struktury mohou mít pole, vlastnosti a události, jakož i statické a nestatické metody. Můžete vytvořit instance struktur, předat jako parametry, uložit je jako lokální proměnné, nebo uložit je do jiného typu hodnoty pole nebo typ odkazu. Struktury také mohou implementovat rozhraní.  
  
 Typy hodnot se také liší od tříd v několika ohledech. První, i když implicitně dědí z <xref:System.ValueType?displayProperty=nameWithType>, nemohou přímo dědit z libovolného typu. Podobně jsou uzavřeny všechny hodnotové typy, což znamená, že žádný jiný typ může být odvozena z nich. Také nevyžadují konstruktory.  
  
 Modul common language runtime pro každý hodnotový typ dodává odpovídající zabalený typ, což je třída, která má stejný stav a chování jako typ hodnoty. Instance hodnotového typu je zabalená, když je předán metodě, která přijímá parametr typu <xref:System.Object?displayProperty=nameWithType>. Je instance nezabalená (to znamená, konvertována z instance třídy zpět na instanci hodnotového typu) když se řízení vrací z volání metody, která akceptuje hodnotu jako parametr odkazem. Některé jazyky vyžadují použití speciální syntaxe, když je požadován; zabalený typ ostatní automaticky použijí zabalený typ, když ho nepotřebují. Když definujete hodnotový typ, definujete zároveň zabalený i nezabalený typ.  
  
<a name="Enumerations"></a>   
### <a name="enumerations"></a>Výčty  
 Výčet (výčtu) je hodnotový typ, který dědí přímo z <xref:System.Enum?displayProperty=nameWithType> a poskytuje alternativní názvy pro hodnoty nadřazeného primitivního typu. Výčtový typ má název základního typu, který musí být jeden z typů předdefinovaných signed nebo unsigned integer (například <xref:System.Byte>, <xref:System.Int32>, nebo <xref:System.UInt64>) a sady polí. Pole jsou statické literální položky, z nichž každá představuje konstantu. Stejná hodnota může být přiřazena více položkám. V takovém případě musíte označit jednu z hodnot jako primární hodnotu výčtu pro reflexe a převodu řetězce.  
  
 Můžete přiřadit hodnotu nadřazeného typu výčtu a naopak (žádné přetypování není požadováno modulem runtime). Můžete vytvořit instanci výčtu a volat metody <xref:System.Enum?displayProperty=nameWithType>, stejně tak jakékoli metody definované u nadřízeného typu výčtu. Nicméně některé jazyky vám pravděpodobně neumožní předat výčet jako parametr, pokud je požadována instance nadřízeného typu (nebo naopak).  
  
 Následující omezení jsou také aplikována na výčty:  
  
-   Nemohou definovat jejich vlastní metody.  
  
-   Nemohou implementovat rozhraní.  
  
-   Nemohou definovat vlastnosti nebo události.  
  
-   Nemohou být obecné, pokud nejsou obecné pouze proto, že jsou vnořené do obecného typu. To znamená že výčet nemůže mít vlastní parametry typu.  
  
    > [!NOTE]
    >  Vnořené typy (včetně výčtů) vytvořené pomocí jazyka Visual Basic, C# a C++ zahrnují parametry typu všech ohraničujících obecných typů a jsou tudíž obecné, i v případě, že nemají vlastní parametry typu. Další informace najdete v tématu "Vnořené typy" <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> téma referenčních informací.  
  
 <xref:System.FlagsAttribute> Atribut označuje zvláštní druh výčtu nazývaný bitové pole. Samotný modul runtime nerozlišuje mezi tradičními výčty a bitová pole, ale váš jazyk může udělat. Když se provádí toto rozlišení, bitové operátory lze používat u bitových polí, ale ne výčtů, kvůli generování nepojmenovaných hodnot. Výčty jsou obecně používány pro seznamy jedinečných prvků, jako je například dny týdne, zemi nebo oblast názvů a tak dále. Bitová pole jsou obecně používána pro seznamy vlastností nebo množství, které mohou nastat dohromady, například `Red And Big And Fast`.  
  
 Následující příklad ukazuje způsob použití bitových polí i tradičních výčtů.  
  
 [!code-csharp[Conceptual.Types.Enum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.enum/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Enum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.enum/vb/example.vb#1)]  
  
<a name="Interfaces"></a>   
### <a name="interfaces"></a>Rozhraní  
 Rozhraní definuje kontrakt, který specifikuje relaci "lze provádět" nebo "má" vztah. Rozhraní jsou často používána k implementaci funkcionality, jako je například porovnávání a řazení ( <xref:System.IComparable> a <xref:System.IComparable%601> rozhraní), testování rovnosti ( <xref:System.IEquatable%601> rozhraní), nebo spočítání položek v kolekci ( <xref:System.Collections.IEnumerable> a <xref:System.Collections.Generic.IEnumerable%601> rozhraní). Rozhraní může mít vlastnosti, metody a události, které se nazývají abstraktní členy; To znamená i když rozhraní definuje členy a jejich podpisy, ponechá je typu, který implementuje rozhraní, aby definoval funkcionalitu každého člena rozhraní. To znamená, že každá třída nebo struktura, která implementuje rozhraní musí poskytnout definici pro abstraktní členy deklarované v rozhraní. Rozhraní může vyžadovat jakákoliv implementující třída nebo struktura také implementovala jedno nebo více rozhraní.  
  
 Následující omezení jsou aplikována na rozhraní:  
  
-   Rozhraní může být deklarováno s jakoukoliv přístupností, ale všechny členy rozhraní musí mít přístupnost public.  
  
-   Rozhraní nemohou definovat konstruktory.  
  
-   Rozhraní nemohou definovat položky.  
  
-   Rozhraní může definovat pouze členy instance. Nemohou definovat statické členy.  
  
 Každý jazyk musí stanovit pravidla mapování implementace na rozhraní, které vyžaduje člen, protože více než jedno rozhraní může deklarovat člena se stejnou signaturou a tyto členy mohou mít odlišnou implementaci.  
  
<a name="Delegates"></a>   
### <a name="delegates"></a>Delegáty  
 Delegáti jsou odkazové typy sloužící k podobnému účelu jako, který ukazatelů na funkce v jazyce C++. Používají se pro zpětné volání funkcí v rozhraní .NET a obslužné rutiny událostí. Na rozdíl od ukazatelů na funkce Delegáti jsou zabezpečeni, ověřitelní a typově bezpečný. Typ delegát může představovat libovolnou metodu instance nebo statickou metodu, která má kompatibilní signaturu.  
  
 Parametr delegáta je kompatibilní s odpovídajícím parametrem metody, pokud typ parametru delegáta více omezující než typ parametru metody, protože toto zaručuje, že argument předaný delegátovi může být předán bezpečně Metoda.  
  
 Podobně návratový typ delegáta je kompatibilní s návratovým typem metody Pokud návratový typ metody více omezující než návratový typ delegáta, protože zaručí se tak, že návratová hodnota metody může být bezpečně přetypovaná na návratový typ elektronické delegáta.  
  
 Například delegát, který má parametr typu <xref:System.Collections.IEnumerable> a návratový typ <xref:System.Object> může představovat metodu, která má parametr typu <xref:System.Object> a návratovou hodnotu typu <xref:System.Collections.IEnumerable>. Další informace a příklady kódu naleznete v tématu <xref:System.Delegate.CreateDelegate%28System.Type%2CSystem.Object%2CSystem.Reflection.MethodInfo%29?displayProperty=nameWithType>.  
  
 Delegát je označován jako vázaný na metodu, kterou představuje. Vedle toho metodu, delegát mohou být vázány na objekt. Objekt představuje první parametr metody a je předán metodě pokaždé, když je vyvolán delegát. Pokud je metoda metodou instance, tak vázaný objekt je předán jako implicitní `this` parametr (`Me` v jazyce Visual Basic); Pokud je metoda statická, objekt je předán jako první formální parametr metody a signatura delegáta musí odpovídat zbývající parametry. Další informace a příklady kódu naleznete v tématu <xref:System.Delegate?displayProperty=nameWithType>.  
  
 Všichni delegáti dědí z <xref:System.MulticastDelegate?displayProperty=nameWithType>, který dědí z <xref:System.Delegate?displayProperty=nameWithType>. Jazyky C#, Visual Basic a C++ neumožňují dědičnost z těchto typů. Místo toho poskytují klíčová slova pro deklarování delegátů.  
  
 Protože delegáti dědí z <xref:System.MulticastDelegate>, tak delegát má seznam vyvolání, což je seznam metod, které delegát reprezentuje a které jsou spouštěny, když je vyvolán delegát. Všechny metody v seznamu obdrží argumenty poskytované při vyvolání delegáta.  
  
> [!NOTE]
>  Návratová hodnota není definována pro delegáta, který má více než jednu metodu v jeho vyvolávacím seznamu i v případě, že delegát má návratový typ.  
  
 V mnoha případech, jako je zpětné volání metod, delegát představuje pouze jednu metodu a jenom akce, které je nutné provést jsou vytvoření delegáta a vyvolání.  
  
 .NET pro delegáty, kteří reprezentují několik metod, poskytuje metody <xref:System.Delegate> a <xref:System.MulticastDelegate> delegovat třídy pro podporu operací, jako je přidání metody do seznamu vyvolání tohoto delegáta ( <xref:System.Delegate.Combine%2A?displayProperty=nameWithType> metoda), odebrání metody ( <xref:System.Delegate.Remove%2A?displayProperty=nameWithType> metoda) a získání seznamu vyvolání ( <xref:System.Delegate.GetInvocationList%2A?displayProperty=nameWithType> metoda).  
  
> [!NOTE]
>  Není nutné používat tyto metody pro delegáty obsluhy událostí v jazyce C#, C++ a Visual Basic, protože tyto jazyky poskytují syntaxi pro přidávání a odebírání obslužných rutin událostí.  
  
 
  
<a name="type_definitions"></a>   
## <a name="type-definitions"></a>Definice typu  
 Definice typu zahrnuje následující položky:  
  
-   Libovolné atributy definované u typu.  
  
-   Přístupnost typu (viditelnost).  
  
-   Název typu.  
  
-   Základní typ tohoto typu.  
  
-   Jakékoliv rozhraní implementované typem.  
  
-   Definice pro každého člena typu.  
  
### <a name="attributes"></a>Atributy  
 Atributy poskytují další metadata definovaná uživatelem. Nejčastěji se používají k ukládání dalších informací o typu v sestavení, nebo chcete změnit chování člena typu buď v době návrhu nebo v běhovém prostředí.  
  
 Atributy jsou samotné třídy, které dědí z <xref:System.Attribute?displayProperty=nameWithType>. Jazyky, které podporují použití atributů mají svou vlastní syntaxi pro aplikování atributů na prvky jazyka. Atributy lze použít na téměř libovolný element jazyka. konkrétní prvky, na které lze aplikovat atribut jsou definovány <xref:System.AttributeUsageAttribute> , která je použita na danou třídu atributů.  
  
### <a name="type-accessibility"></a>Přístupnost typu  
 Všechny typy mají modifikátor, který řídí jejich přístupnost z jiných typů. Následující tabulka popisuje přístupnosti typu podporované modulem runtime.  
  
|Usnadnění|Popis|  
|-------------------|-----------------|  
|public|Typ je přístupný všem sestavením.|  
|sestavení|Typ je přístupný pouze uvnitř jeho sestavení.|  
  
 Přístupnost vnořeného typu závisí na jeho doméně přístupnosti, která je určena deklarovanou přístupností člena a doménou přístupnosti bezprostředně nadřazeného typu. Doména přístupnosti vnořeného typu však nesmí přesáhnout přístupnost nadřazeného typu.  
  
 Doména přístupnosti vnořeného člena `M` deklarovaného v typu `T` v rámci programu `P` je definována takto (konstatujme, že `M` může být sám typ):  
  
-   Pokud je deklarovaná přístupnost člena `M` je `public`, tak doména přístupnosti člena `M` je doména přístupnosti člena `T`.  
  
-   Pokud je deklarovaná přístupnost člena `M` je `protected internal`, tak doména přístupnosti člena `M` je průsečík domény přístupnosti typu `T` s textem programu `P` a textem programu libovolného typu odvozené z `T` deklarované mimo `P`.  
  
-   Pokud je deklarovaná přístupnost člena `M` je `protected`, tak doména přístupnosti člena `M` je průsečík domény přístupnosti typu `T` s textem programu `T` a libovolného typu odvozeného z `T`.  
  
-   Pokud je deklarovaná přístupnost člena `M` je `internal`, tak doména přístupnosti člena `M` je průsečík domény přístupnosti typu `T` s textem programu `P`.  
  
-   Pokud je deklarovaná přístupnost člena `M` je `private`, tak doména přístupnosti člena `M` je text programu `T`.  
  
### <a name="type-names"></a>Názvy typů  
 Obecný systém typů vynucuje pouze dvě omezení pro názvy:  
  
-   Všechny názvy jsou kódovány jako řetězce znaků Unicode (16 bitů).  
  
-   Názvy nejsou oprávněny mít embedded (16-bit) hodnotu 0x0000.  
  
 Většina jazyků však zavádí další omezení pro názvy typů. Všechna porovnání jsou prováděna byte po bajtu a proto jsou malá a velká písmena a nezávislý na národním prostředí.  
  
 Přestože typ může odkazovat na typy z jiných modulů a sestavení, musí být typu plně definován uvnitř jednoho modulu rozhraní .NET. (V závislosti na podpoře kompilátoru však může být rozdělen do více souborů zdrojového kódu.) Názvy typů musí být jedinečné uvnitř oboru názvů. K byl typ plně identifikován, musí být kvalifikován názvem typu obor názvů, který obsahuje implementaci daného typu.  
  
### <a name="base-types-and-interfaces"></a>Základní typy a rozhraní  
 Typ může zdědit hodnoty a chování od jiného typu. Obecný systém typů neumožňuje typům dědit z více než jednoho základního typu.  
  
 Typ může implementovat libovolný počet rozhraní. Implementovat rozhraní, typ musí implementovat všechny virtuální členy rozhraní. Virtuální metoda může být implementována odvozeným typem a vyvolána staticky nebo dynamicky.  
  
  
  
<a name="type_members"></a>   
## <a name="type-members"></a>Členy typu  
 Modul runtime umožňuje definovat členy vašeho typu, který určuje chování a stav tohoto typu. Členy typu zahrnují následující:  
  
-   [Pole](#Fields)  
  
-   [Vlastnosti](#Properties)  
  
-   [Metody](#Methods)  
  
-   [Konstruktory](#Constructors)  
  
-   [Události](#Events)  
  
-   [Vnořené typy](#NestedTypes)  
  
<a name="Fields"></a>   
### <a name="fields"></a>Pole  
 Položka popisuje a obsahuje část stavu typu. Pole může být libovolného typu podporované modulem runtime. Nejčastěji jsou položky buď `private` nebo `protected`, takže jsou přístupné pouze v rámci třídy nebo z odvozené třídy. Pokud hodnota pole může být změněna mimo její typ, se obvykle používá přistupující objekt množiny vlastností. Veřejně vystavené položky jsou obvykle jen pro čtení a mohou být dvou typů:  
  
-   Konstanty, jejichž hodnoty jsou přiřazeny v době návrhu. Toto jsou statické členy třídy, i když nejsou definovány pomocí `static` (`Shared` v jazyce Visual Basic) – klíčové slovo.  
  
-   Jen pro čtení proměnné, jejichž hodnoty mohou být přiřazeny v konstruktoru třídy.  
  
 Následující příklad znázorňuje tyto dva způsoby použití položek pole jen pro čtení.  
  
 [!code-csharp[Conceptual.Types.Members.Fields#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.fields/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Fields#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.fields/vb/example.vb#1)]  
  
<a name="Properties"></a>   
### <a name="properties"></a>Vlastnosti  
 Vlastnosti pojmenovávají hodnotu nebo stav typu a definuje metody pro získání nebo nastavení hodnoty vlastnosti. Vlastnosti mohou být primitivní typy, kolekce primitivních typů, uživatelem definované typy nebo kolekce uživatelem definovaných typů. Vlastnosti se často používají k zachovat nezávislé veřejného rozhraní typu od aktuální reprezentace typu. Toto umožňuje vlastnostem vyjadřovat hodnoty, které nejsou uloženy přímo ve třídě (například, když vlastnost vrací vypočítanou hodnotu) nebo provádět ověření před hodnoty jsou přiřazeny k privátním položkám. Následující příklad znázorňuje druhý případ.  
  
 [!code-csharp[Conceptual.Types.Members.Properties#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.properties/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Properties#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.properties/vb/example.vb#1)]  
  
 Kromě zahrnutí samotné vlastnosti, obsahuje Microsoft intermediate language (MSIL) pro typ obsahující čitelnou vlastnost `get_` *propertyname* metoda a jazyk MSIL pro typ, který obsahuje zapisovatelný obsahuje vlastnosti `set_` *propertyname* metody.  
  
<a name="Methods"></a>   
### <a name="methods"></a>Metody  
 Metoda popisuje operace, které jsou k dispozici u typu. Signatura metody specifikuje přípustné typy všech jejích parametrů a její návratovou hodnotu.  
  
 Přestože většina metod definuje přesný počet parametrů požadovaných pro volání metody, některé metody podporují proměnný počet parametrů. Výsledný deklarovaný parametr těchto metod je označen <xref:System.ParamArrayAttribute> atribut. Kompilátory jazyka obvykle poskytují klíčové slovo, jako například `params` v jazyce C# a `ParamArray` v jazyce Visual Basic, který činí explicitní použití atributu <xref:System.ParamArrayAttribute> zbytečné.  
  
<a name="Constructors"></a>   
### <a name="constructors"></a>Konstruktory  
 Konstruktor je zvláštní druh metody, která vytváří nové instance třídy nebo struktury. Stejně jako jakákoli jiná metoda konstruktor může obsahovat parametry; ale konstruktory nemají žádnou návratovou hodnotu (to znamená, že vrací `void`).  
  
 Pokud zdrojový kód třídy explicitně nedefinuje konstruktor, kompilátor obsahuje výchozí konstruktor (bez parametrů). Nicméně pokud zdrojový kód třídy definuje pouze konstruktor s parametry, kompilátory jazyků Visual Basic a C# negenerují tento konstruktor bez parametrů.  
  
 Pokud zdrojový kód struktury definuje konstruktory, musí být parametrizovány; struktura nemůže definovat výchozí konstruktor (bez parametrů) a kompilátory negenerují bezparametrické konstruktory pro struktury nebo jiné hodnotové typy. Všechny hodnotové typy mají implicitní výchozí konstruktor. Tento konstruktor je implementován modulem common language runtime a inicializuje všechny položky struktury na jejich výchozí hodnoty.  
  
<a name="Events"></a>   
### <a name="events"></a>Události  
 Událost definuje situaci, která může být odpovězeno a definuje metody pro přihlášení k odběru, ruší registraci a vyvolání události. Události jsou často používají k informovaly jiné typy o změně stavu. Další informace najdete v tématu [události](../../../docs/standard/events/index.md).  
  
<a name="NestedTypes"></a>   
### <a name="nested-types"></a>Vnořené typy  
 Vnořený typ je typ, který je členem některého jiného typu. Vnořené typy by měly být úzce spojeny s jejich nadřazeným typem a nesmí být užitečné jako všeobecný typ. Vnořené typy jsou užitečné, pokud je deklarující typ používá a vytváří instance vnořeného typu a použití vnořeného typu není zveřejněno ve veřejných členech.  
  
 Vnořené typy jsou matoucí pro některé vývojáře a neměly by být veřejně viditelné pokud neexistuje závažný důvod pro viditelnost. V dobře navržené knihovně by vývojáři by měli mít jen zřídka použít vnořené typy pro vytvoření instancí objektů nebo deklaraci proměnných.  
  
  
  
<a name="characteristics_of_type_members"></a>   
## <a name="characteristics-of-type-members"></a>Charakteristiky členů typu  
 Obecný systém typů umožňuje členům typu mít různé vlastnosti; jazycích však není požadována podpora všech těchto vlastností. Následující tabulka popisuje vlastnosti členů.  
  
|Vlastnost|Můžete použít na|Popis|  
|--------------------|------------------|-----------------|  
|abstract|Metody, vlastnosti a události|Typ neposkytuje implementaci metody. Typy, které dědí nebo implementují abstraktní metody musí poskytnout implementaci pro metodu. Jedinou výjimkou je, pokud odvozený typ je abstraktní typ. Všechny abstraktní metody jsou virtuální.|  
|privátní, řady, sestavení, řada a sestavení, řada nebo sestavení nebo veřejné|Všechny|Definuje dostupnost člena:<br /><br /> private<br /> Přístupný pouze uvnitř stejného typu jako člen nebo uvnitř vnořeného typu.<br /><br /> Řada<br /> Přístupný uvnitř stejného typu jako člen a z odvozeného typu, které z něj dědí.<br /><br /> sestavení<br /> Přístupný pouze v sestavení, ve kterém je typ definován.<br /><br /> family a assembly<br /> Přístupný pouze z typů, které jsou způsobilé pro family a assembly přístup.<br /><br /> řada nebo sestavení<br /> Přístupný pouze z typů, které jsou způsobilé pro family nebo assembly přístup.<br /><br /> public<br /> Přístupné z libovolného typu.|  
|finální|Metody, vlastnosti a události|Virtuální metoda nemůže být přepsána v odvozeném typu.|  
|pouze inicializace|Pole|Hodnota se dá inicializovat jenom a nelze ji po inicializaci zapsat.|  
|instance|Pole, metody, vlastnosti a události|Pokud člen není označen jako `static` (C# a C++), `Shared` (Visual Basic), `virtual` (C# a C++), nebo `Overridable` (Visual Basic), je členem instance (neexistuje žádné klíčové slovo instance). Bude tolik kopií takovýchto členů v paměti jsou objekty, které ji používají.|  
|literál|Pole|Hodnota přiřazená k položce je pevná hodnota, známá v době kompilace předdefinovaného hodnotového typu. Položky typu literál jsou někdy označovány jako konstanty.|  
|newslot nebo přepsání|Všechny|Definuje způsob interakce člena se zděděnými členy, které mají stejnou signaturu:<br /><br /> newslot<br /> Skryje zděděné členy, které mají stejnou signaturu.<br /><br /> override<br /> Nahradí definici zděděné virtuální metody.<br /><br /> Výchozí hodnota je newslot.|  
|static|Pole, metody, vlastnosti a události|Člen náleží k typu, který je definován a ne k určité instanci typu; člen existuje i v případě, že instance typu není vytvořena a je sdílen mezi všemi instancemi typu.|  
|virtual|Metody, vlastnosti a události|Metoda může být implementována odvozeným typem a vyvolána staticky nebo dynamicky. Pokud je použito dynamické vyvolání, typu instance, která provádí volání v době běhu (spíše než známý typ v době kompilace) určuje, která implementace metody je volána. Pro virtuální metoda vyvolána staticky, možná muset proměnné přetypovat na typ, který používá požadovanou verzi metody.|  
  
### <a name="overloading"></a>Přetížení  
 Každý člen typu má jedinečnou signaturu. Signatury metod se skládají z názvu metody a seznamu parametrů (pořadí a typ argumentů metody). V rámci typu lze definovat více metod se stejným názvem, tak dlouho, dokud se liší jejich podpisy. Když jsou definovány dvě nebo více metod se stejným názvem, se říká, že metoda přetížena. Například v <xref:System.Char?displayProperty=nameWithType>, <xref:System.Char.IsDigit%2A> přetížené metody. Přijímá jednu metodu <xref:System.Char>. Tato metoda přebírá <xref:System.String> a <xref:System.Int32>.  
  
> [!NOTE]
>  Návratový typ není považováno za součást signatury metody. To znamená, že metody nemohou být přetíženy, pokud se liší pouze návratovým typem.  
  
### <a name="inheriting-overriding-and-hiding-members"></a>Dědění, přepisování a skrývání členů  
 Odvozený typ zdědí všechny členy jeho rodičovského typu; To znamená, že tyto členy jsou definovány tak k dispozici pro odvozený typ. Chování a vlastnosti zděděných členů může být upraveny dvěma způsoby:  
  
-   Odvozený typ může skrýt zděděný člen tak, že definujete nového člena se stejným podpisem. Toto může být provedeno, aby z dříve veřejného člena soukromý nebo definovat nové chování pro zděděnou metodu, která je označena jako `final`.  
  
-   Odvozený typ může přepsat zděděnou virtuální metodu. Přepsání metody poskytuje novou definici metody, která bude volána na základě typu hodnoty v době běhu, nikoli typu proměnné v době kompilace znám. Metoda může přepsat virtuální metodu pouze v případě, že virtuální metoda není označena jako `final` a nová metoda je přinejmenším stejně dostupná jako virtuální metody.  
  
## <a name="see-also"></a>Viz také:

- [Prohlížeč rozhraní API .NET](/dotnet/api)  
- [Modul Common Language Runtime](../../../docs/standard/clr.md)  
- [Převod typů v rozhraní .NET](../../../docs/standard/base-types/type-conversion.md)
