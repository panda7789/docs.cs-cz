---
title: Obecný systém typů
description: Informace o systému typů v rozhraní .NET.
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
ms.openlocfilehash: c574719da9b89b468b92b042e1f2b5b10fbe3c0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400489"
---
# <a name="common-type-system"></a>Obecný systém typů
Společný systém typů definuje, jak jsou typy deklarovány, používány a spravovány v prostředí common language runtime a je také důležitou součástí podpory runtime pro integraci mezi jazyky. Systém běžného typu provádí následující funkce:  
  
- Vytvoří rámec, který pomáhá povolit integraci mezi jazyky, bezpečnost typů a provádění vysoce výkonných kódů.  
  
- Poskytuje objektově orientovaný model, který podporuje úplnou implementaci mnoha programovacích jazyků.  
  
- Definuje pravidla, která musí jazyky dodržovat, což pomáhá zajistit, aby objekty napsané v různých jazycích mohly vzájemně komunikovat.  
  
- Poskytuje knihovnu, která obsahuje primitivní <xref:System.Boolean>datové <xref:System.Byte> <xref:System.Char>typy <xref:System.Int32>(například , , , a <xref:System.UInt64>) používané při vývoji aplikací.  
  
 Toto téma obsahuje následující oddíly:  
  
- [Typy v rozhraní .NET](#types_in_the_net_framework)  
  
- [Definice typů](#type_definitions)  
  
- [Členy typu](#type_members)  
  
- [Charakteristika typových členů](#characteristics_of_type_members)  
  
<a name="types_in_the_net_framework"></a>
## <a name="types-in-net"></a>Typy v rozhraní .NET  
 Všechny typy v rozhraní .NET jsou typy hodnot nebo typy odkazů.  
  
 Typy hodnot jsou datové typy, jejichž objekty jsou reprezentovány skutečnou hodnotou objektu. Pokud je instanci typu hodnoty přiřazena proměnné, je této proměnné přidělena nová kopie hodnoty.  
  
 Referenční typy jsou datové typy, jejichž objekty jsou reprezentovány odkazem (podobně jako ukazatel) na skutečnou hodnotu objektu. Pokud je proměnná přiřazena typu odkazu, tato proměnná odkazuje (odkazuje na) původní hodnotu. Není provedena žádná kopie.  
  
 Běžný systém typů v rozhraní .NET podporuje následujících pět kategorií typů:  
  
- [Třídy](#Classes)  
  
- [Struktury](#Structures)  
  
- [Výčty](#Enumerations)  
  
- [Rozhraní](#Interfaces)  
  
- [Delegáty](#Delegates)  
  
<a name="Classes"></a>
### <a name="classes"></a>Třídy  
 Třída je typ odkazu, který lze odvodit přímo z jiné <xref:System.Object?displayProperty=nameWithType>třídy a který je implicitně odvozen z . Třída definuje operace, které může objekt (což je instance třídy) provádět (metody, události nebo vlastnosti) a data, která objekt obsahuje (pole). Přestože třída obecně obsahuje definici a implementaci (na rozdíl od rozhraní, například, které obsahují pouze definici bez implementace), může mít jeden nebo více členů, které nemají žádnou implementaci.  
  
 Následující tabulka popisuje některé charakteristiky, které může mít třída. Každý jazyk, který podporuje runtime poskytuje způsob, jak označit, že člen třídy nebo třídy má jednu nebo více z těchto vlastností. Jednotlivé programovací jazyky, které cílí na rozhraní .NET, však nemusí zpřístupnit všechny tyto vlastnosti.  
  
|Charakteristika|Popis|  
|--------------------|-----------------|  
|sealed|Určuje, že z tohoto typu nelze odvodit jinou třídu.|  
|implements|Označuje, že třída používá jedno nebo více rozhraní tím, že poskytuje implementace členů rozhraní.|  
|abstract|Označuje, že nelze vytvořit instanci třídy. Chcete-li jej použít, musíte z něj odvodit jinou třídu.|  
|Dědí|Označuje, že instance třídy lze použít kdekoli základní třídy je určena. Odvozená třída, která dědí ze základní třídy, může použít implementaci všech veřejných členů poskytovaných základní třídou nebo odvozená třída může přepsat implementaci veřejných členů s vlastní implementací.|  
|exportovány nebo neexportovány|Označuje, zda je třída viditelná mimo sestavení, ve kterém je definována. Tato charakteristika platí pouze pro třídy nejvyšší úrovně a nikoli pro vnořené třídy.|  
  
> [!NOTE]
> Třída může být také vnořena do nadřazené třídy nebo struktury. Vnořené třídy mají také vlastnosti členů. Další informace naleznete v [tématu Vnořené typy](#NestedTypes).  
  
 Členové třídy, které nemají žádnou implementaci, jsou abstraktní členy. Třída, která má jeden nebo více abstraktních členů, je sama abstraktní; nové instance nelze vytvořit. Některé jazyky, které cílí na runtime, umožňují označit třídu jako abstraktní, i když žádný z jeho členů není abstraktní. Abstraktní třídu můžete použít, pokud chcete zapouzdřit základní sadu funkcí, které odvozené třídy mohou dědit nebo přepsat, pokud je to vhodné. Třídy, které nejsou abstraktní, jsou označovány jako konkrétní třídy.  
  
 Třída může implementovat libovolný počet rozhraní, ale může dědit pouze <xref:System.Object?displayProperty=nameWithType>z jedné základní třídy kromě , ze které všechny třídy dědí implicitně. Všechny třídy musí mít alespoň jeden konstruktor, který inicializuje nové instance třídy. Pokud explicitně nedefinujete konstruktor, většina kompilátorů automaticky poskytne konstruktor bez parametrů.  
  
<a name="Structures"></a>
### <a name="structures"></a>Struktury  
 Struktura je typ hodnoty, který je <xref:System.ValueType?displayProperty=nameWithType>implicitně odvozen z <xref:System.Object?displayProperty=nameWithType>, který je odvozen z . Struktura je velmi užitečná pro reprezentaci hodnot, jejichž požadavky na paměť jsou malé, a pro předávání hodnot jako parametrů podle hodnoty metodám, které mají parametry silného typu. V rozhraní .NET jsou<xref:System.Boolean>všechny <xref:System.Byte> <xref:System.Char>primitivní <xref:System.DateTime> <xref:System.Decimal>datové <xref:System.Double> <xref:System.Int16>typy <xref:System.Int32> <xref:System.Int64>( <xref:System.SByte> <xref:System.Single>, <xref:System.UInt16> <xref:System.UInt32>, <xref:System.UInt64>, , , , , , , , , a ) definovány jako struktury.  
  
 Stejně jako třídy, struktury definovat data (pole struktury) a operace, které lze provést na tato data (metody struktury). To znamená, že můžete volat metody na struktury, <xref:System.Object?displayProperty=nameWithType> včetně <xref:System.ValueType?displayProperty=nameWithType> virtuální metody definované na a třídy a všechny metody definované na typ hodnoty sám. Jinými slovy, struktury mohou mít pole, vlastnosti a události, stejně jako statické a nestatické metody. Můžete vytvořit instance struktur, předat je jako parametry, uložit je jako místní proměnné nebo je uložit do pole jiného typu hodnoty nebo typu odkazu. Struktury mohou také implementovat rozhraní.  
  
 Typy hodnot se také liší od tříd v několika ohledech. Za prvé, i když <xref:System.ValueType?displayProperty=nameWithType>implicitně dědí z , nemohou přímo dědit z libovolného typu. Podobně jsou zapečetěny všechny typy hodnot, což znamená, že z nich nelze odvodit žádný jiný typ. Také nevyžadují konstruktory.  
  
 Pro každý typ hodnoty, za běhu společného jazyka poskytuje odpovídající zabalený typ, což je třída, která má stejný stav a chování jako typ hodnoty. Instance typu hodnoty je zabalena, když je předána metodě, <xref:System.Object?displayProperty=nameWithType>která přijímá parametr typu . Je unboxed (to znamená, převedeny z instance třídy zpět na instanci typu hodnoty) při ovládacíprvek vrátí z volání metody, která přijímá typ hodnoty jako parametr odkaz. Některé jazyky vyžadují použití speciální syntaxe, pokud je vyžadován typ v rámečku; ostatní automaticky používají typ v rámečku, když je to potřeba. Když definujete typ hodnoty, definujete typ zabalený i nezabalený.  
  
<a name="Enumerations"></a>
### <a name="enumerations"></a>Výčty  
 Výčt (výčt) je typ hodnoty, který <xref:System.Enum?displayProperty=nameWithType> dědí přímo z a který poskytuje alternativní názvy pro hodnoty základníprimitivní typ. Typ výčtu má název, základní typ, který musí být jedním z předdefinovaných podepsaných <xref:System.Byte> <xref:System.Int32>nebo <xref:System.UInt64>nepodepsaných celočíselných typů (například , , nebo ) a sadu polí. Pole jsou statická literálová pole, z nichž každé představuje konstantu. Stejnou hodnotu lze přiřadit k více polím. V takovém případě je nutné označit jednu z hodnot jako primární hodnotu výčtu pro převod odrazu a převod řetězce.  
  
 Můžete přiřadit hodnotu základního typu výčtu a naopak (žádný přetypování je vyžadováno runtime). Můžete vytvořit instanci výčtu a volat <xref:System.Enum?displayProperty=nameWithType>metody , stejně jako všechny metody definované na základní typ výčtu. Některé jazyky však nemusí nechat předat výčet jako parametr, pokud je vyžadována instance základního typu (nebo naopak).  
  
 Následující další omezení platí pro výčty:  
  
- Nemohou definovat své vlastní metody.  
  
- Nemohou implementovat rozhraní.  
  
- Nemohou definovat vlastnosti nebo události.  
  
- Nemohou být obecné, pokud nejsou obecné pouze proto, že jsou vnořeny do obecného typu. To znamená, že výčet nemůže mít vlastní parametry typu.  
  
    > [!NOTE]
    > Vnořené typy (včetně výčtů) vytvořené pomocí jazyka Visual Basic, C# a C++ zahrnují parametry typu všech ohraničujících obecných typů a jsou proto obecné, i když nemají vlastní parametry typu. Další informace naleznete v tématu "Vnořené typy" v referenčním tématu. <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType>  
  
 Atribut <xref:System.FlagsAttribute> označuje zvláštní druh výčtu nazývaný bitové pole. Samotný běh ový čas nerozlišuje mezi tradičními výčty a bitovými poli, ale váš jazyk tak může učinit. Při tomto rozlišení bitové operátory lze použít na bitová pole, ale ne na výčtu, ke generování nepojmenovaných hodnot. Výčty se obvykle používají pro seznamy jedinečných prvků, jako jsou dny v týdnu, názvy zemí nebo oblastí a tak dále. Bitová pole se obvykle používají pro seznamy vlastností nebo `Red And Big And Fast`množství, ke kterým může dojít v kombinaci, například .  
  
 Následující příklad ukazuje, jak používat bitová pole a tradiční výčty.  
  
 [!code-csharp[Conceptual.Types.Enum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.enum/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Enum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.enum/vb/example.vb#1)]  
  
<a name="Interfaces"></a>
### <a name="interfaces"></a>Rozhraní  
 Rozhraní definuje smlouvu, která určuje vztah "může udělat" nebo "má" vztah. Rozhraní se často používají k implementaci funkce, jako je <xref:System.IComparable> například porovnání a řazení <xref:System.IComparable%601> (a rozhraní), testování <xref:System.IEquatable%601> rovnosti (rozhraní) <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> nebo výčet položek v kolekci (a rozhraní). Rozhraní mohou mít vlastnosti, metody a události, které jsou všechny abstraktní členy; to znamená, že i když rozhraní definuje členy a jejich podpisy, ponechá na typu, který implementuje rozhraní k definování funkce každého člena rozhraní. To znamená, že všechny třídy nebo struktury, která implementuje rozhraní musí dodávat definice pro abstraktní členy deklarované v rozhraní. Rozhraní může vyžadovat všechny implementující třídy nebo struktury také implementovat jedno nebo více dalších rozhraní.  
  
 Následující omezení platí pro rozhraní:  
  
- Rozhraní lze deklarovat s libovolnou přístupnost, ale všechny členy rozhraní musí mít veřejnou přístupnost.  
  
- Rozhraní nelze definovat konstruktory.  
  
- Rozhraní nemohou definovat pole.  
  
- Rozhraní mohou definovat pouze členy instance. Nemohou definovat statické členy.  
  
 Každý jazyk musí obsahovat pravidla pro mapování implementace na rozhraní, které vyžaduje člena, protože více než jedno rozhraní může deklarovat člena se stejným podpisem a tito členové mohou mít samostatné implementace.  
  
<a name="Delegates"></a>
### <a name="delegates"></a>Delegáty  
 Delegáti jsou typy odkazů, které slouží k účelu podobnému ukazatelům funkce v jazyce C++. Používají se pro obslužné rutiny událostí a funkce zpětného volání v rozhraní .NET. Na rozdíl od ukazatelů funkce delegáti jsou zabezpečené, ověřitelné a typ bezpečné. Typ delegáta může představovat libovolnou metodu instance nebo statickou metodu, která má kompatibilní podpis.  
  
 Parametr delegáta je kompatibilní s odpovídajícím parametrem metody, pokud je typ parametru delegáta více omezující než typ parametru metody, protože to zaručuje, že argument předaný delegátovi může být bezpečně předán metodou.  
  
 Podobně návratový typ delegáta je kompatibilní s návratovým typem metody, pokud je návratový typ metody více omezující než návratový typ delegáta, protože to zaručuje, že vrácená hodnota metody může být bezpečně přetypována na return typu delegáta.  
  
 Například delegát, který má parametr <xref:System.Collections.IEnumerable> typu a <xref:System.Object> návratový typ může představovat <xref:System.Object> metodu, která <xref:System.Collections.IEnumerable>má parametr typu a vrácenou hodnotu typu . Další informace a ukázkový <xref:System.Delegate.CreateDelegate%28System.Type%2CSystem.Object%2CSystem.Reflection.MethodInfo%29?displayProperty=nameWithType>kód naleznete v tématu .  
  
 Delegát je prý vázán na metodu, kterou představuje. Kromě toho, že je vázán na metodu, může být delegát vázán na objekt. Objekt představuje první parametr metody a je předán metodě pokaždé, když je vyvolán delegát. Pokud je metoda metoda instance, vázaný objekt je `this` předán`Me` jako implicitní parametr (v jazyce Visual Basic); Pokud je metoda statická, je objekt předán jako první formální parametr metody a podpis delegáta musí odpovídat zbývajícím parametrům. Další informace a ukázkový <xref:System.Delegate?displayProperty=nameWithType>kód naleznete v tématu .  
  
 Všichni delegáti <xref:System.MulticastDelegate?displayProperty=nameWithType>dědí z <xref:System.Delegate?displayProperty=nameWithType>, který dědí z . Jazyky Jazyka C#, Visual Basic a C++ neumožňují dědičnost z těchto typů. Místo toho poskytují klíčová slova pro deklarování delegátů.  
  
 Vzhledem k <xref:System.MulticastDelegate>tomu, že delegáti dědí z , delegát má seznam vyvolání, což je seznam metod, které delegát představuje a které jsou provedeny při vyvolání delegáta. Všechny metody v seznamu obdrží argumenty zadané při vyvolání delegáta.  
  
> [!NOTE]
> Vrácená hodnota není definována pro delegáta, který má více než jednu metodu v seznamu vyvolání, i v případě, že delegát má návratový typ.  
  
 V mnoha případech, například pomocí metod zpětného volání, delegát představuje pouze jednu metodu a jediné akce, které musíte provést, jsou vytvoření delegáta a jeho vyvolání.  
  
 Pro delegáty, kteří představují více metod, .NET <xref:System.Delegate> poskytuje metody a <xref:System.MulticastDelegate> delegovat třídy pro podporu <xref:System.Delegate.Combine%2A?displayProperty=nameWithType> operací, jako je <xref:System.Delegate.Remove%2A?displayProperty=nameWithType> například přidání metody do <xref:System.Delegate.GetInvocationList%2A?displayProperty=nameWithType> seznamu vyvolání delegáta (metoda), odebrání metody (metoda) a získání seznamu vyvolání (metoda).  
  
> [!NOTE]
> Není nutné používat tyto metody pro delegáty obslužné rutiny událostí v jazyce C#, C++ a Visual Basic, protože tyto jazyky poskytují syntaxi pro přidání a odebrání obslužných rutin událostí.  

<a name="type_definitions"></a>
## <a name="type-definitions"></a>Definice typů  
 Definice typu zahrnuje následující:  
  
- Všechny atributy definované na typu.  
  
- Přístupnost typu (viditelnost).  
  
- Název typu.  
  
- Základní typ typu.  
  
- Všechna rozhraní implementovaná typem.  
  
- Definice pro každý člen typu.  
  
### <a name="attributes"></a>Atributy  
 Atributy poskytují další uživatelem definovaná metadata. Nejčastěji se používají k ukládání dalších informací o typu v jeho sestavení nebo k úpravě chování člena typu v návrhovém nebo run-time prostředí.  
  
 Atributy jsou samy třídy, které dědí z <xref:System.Attribute?displayProperty=nameWithType>. Jazyky, které podporují použití atributů, mají vlastní syntaxi pro použití atributů na element jazyka. Atributy lze použít pro téměř jakýkoli prvek jazyka; specifické prvky, na které lze použít <xref:System.AttributeUsageAttribute> atribut, jsou definovány tím, který je použit pro tuto třídu atributu.  
  
### <a name="type-accessibility"></a>Přístupnost typu  
 Všechny typy mají modifikátor, který řídí jejich usnadnění přístupu z jiných typů. Následující tabulka popisuje přístupy typu podporované modulem runtime.  
  
|Přístupnost|Popis|  
|-------------------|-----------------|  
|public|Typ je přístupný všemi sestaveními.|  
|sestavení|Typ je přístupný pouze z jeho sestavení.|  
  
 Usnadnění vnořeného typu závisí na jeho doméně usnadnění přístupu, která je určena deklarovanou přístupností člena i doménou usnadnění typu bezprostředně obsahujícího. Doména usnadnění vnořeného typu však nesmí překročit doménu obsahujícího typu.  
  
 Doména usnadnění vnořeného `M` člena `T` deklarovaného v typu v rámci programu `P` je definována následujícím způsobem (s ohledem na to, že `M` může být sám typ):  
  
- Pokud `M` je `public`deklarovaná přístupnost `M` , doména `T`usnadnění je doménou usnadnění .  
  
- Pokud `M` `protected internal`je deklarovaná přístupnost `M` , doména usnadnění `T` je průsečík `P` domény usnadnění s textem `T` programu `P`a textem programu libovolného typu odvozeného z deklarovaného vnějšku .  
  
- Pokud `M` je `protected`deklarovaná přístupnost `M` , doména usnadnění `T` je průsečík `T` domény usnadnění s `T`textem programu a libovolným typem odvozeným od .  
  
- Pokud `M` je `internal`deklarovaná přístupnost `M` , doména usnadnění `T` je průsečík `P`domény usnadnění s textem programu .  
  
- Pokud `M` je `private`deklarovaná přístupnost `M` , doména `T`usnadnění je text programu .  
  
### <a name="type-names"></a>Názvy typů  
 Společný systém typů ukládá pouze dvě omezení na názvy:  
  
- Všechny názvy jsou kódovány jako řetězce znaků Unicode (16 bitů).  
  
- Názvy nesmí mít vloženou (16bitovou) hodnotu 0x0000.  
  
 Většina jazyků však ukládají další omezení názvů typů. Všechna porovnání se provádí na základě bajt po bajtu, a proto jsou malá a velká písmena a národní prostředí nezávislé.  
  
 Přestože typ může odkazovat na typy z jiných modulů a sestavení, musí být typ plně definován v rámci jednoho modulu .NET. (V závislosti na podpoře kompilátoru však může být rozdělena do více souborů zdrojového kódu.) Názvy typů musí být jedinečné pouze v rámci oboru názvů. Chcete-li plně identifikovat typ, musí být název typu kvalifikován oborem názvů, který obsahuje implementaci typu.  
  
### <a name="base-types-and-interfaces"></a>Základní typy a rozhraní  
 Typ může dědit hodnoty a chování z jiného typu. Běžný systém typů neumožňuje, aby typy dědily z více než jednoho základního typu.  
  
 Typ může implementovat libovolný počet rozhraní. Chcete-li implementovat rozhraní, typ musí implementovat všechny virtuální členy tohoto rozhraní. Virtuální metoda může být implementována odvozeným typem a může být vyvolána staticky nebo dynamicky.  

<a name="type_members"></a>
## <a name="type-members"></a>Členy typu  
 Runtime umožňuje definovat členy typu, který určuje chování a stav typu. Mezi členy typu patří následující:  
  
- [Pole](#Fields)  
  
- [Vlastnosti](#Properties)  
  
- [Metody](#Methods)  
  
- [Konstruktory](#Constructors)  
  
- [Akce](#Events)  
  
- [Vnořené typy](#NestedTypes)  
  
<a name="Fields"></a>
### <a name="fields"></a>Fields (Pole)  
 Pole popisuje a obsahuje část stavu typu. Pole mohou být libovolného typu podporovaného modulem runtime. Nejčastěji pole jsou `private` buď `protected`nebo , tak, aby byly přístupné pouze z v rámci třídy nebo z odvozené třídy. Pokud hodnotu pole lze změnit z mimo jeho typ, obvykle se používá přistupující objekt sady vlastností. Veřejně exponovaná pole jsou obvykle jen pro čtení a mohou být dvou typů:  
  
- Konstanty, jejichž hodnota je přiřazena v době návrhu. Jedná se o statické členy třídy, i `static` `Shared` když nejsou definovány pomocí (v jazyce Visual Basic).  
  
- Proměnné jen pro čtení, jejichž hodnoty lze přiřadit v konstruktoru třídy.  
  
 Následující příklad ilustruje tyto dvě použití polí jen pro čtení.  
  
 [!code-csharp[Conceptual.Types.Members.Fields#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.fields/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Fields#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.fields/vb/example.vb#1)]  
  
<a name="Properties"></a>
### <a name="properties"></a>Vlastnosti  
 Vlastnost pojmenuje hodnotu nebo stav typu a definuje metody pro získání nebo nastavení hodnoty vlastnosti. Vlastnosti mohou být primitivní typy, kolekce primitivních typů, uživatelem definované typy nebo kolekce uživatelem definovaných typů. Vlastnosti se často používají k udržení veřejné rozhraní typu nezávislé na skutečné reprezentaci typu. To umožňuje vlastnosti odrážet hodnoty, které nejsou přímo uloženy ve třídě (například když vlastnost vrátí vypočítanou hodnotu) nebo provést ověření před hodnoty jsou přiřazeny k soukromým polím. Následující příklad ilustruje druhý vzor.  
  
 [!code-csharp[Conceptual.Types.Members.Properties#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.properties/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Properties#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.properties/vb/example.vb#1)]  
  
 Kromě zahrnutí samotné vlastnosti, zprostředkující jazyk Společnosti Microsoft (MSIL) pro `get_`typ, který obsahuje čitelnou vlastnost, obsahuje metodu *propertyname* a MSIL pro typ, který obsahuje zapisovatelnou vlastnost, obsahuje metodu `set_` *propertyname.*  
  
<a name="Methods"></a>
### <a name="methods"></a>Metody  
 Metoda popisuje operace, které jsou k dispozici na typu. Podpis metody určuje povolené typy všech jejích parametrů a její vrácené hodnoty.  
  
 Ačkoli většina metod definuje přesný počet parametrů požadovaných pro volání metod, některé metody podporují proměnný počet parametrů. Konečný deklarovaný parametr těchto <xref:System.ParamArrayAttribute> metod je označen atributem. Kompilátory jazyka obvykle poskytují `params` klíčové slovo, `ParamArray` například v jazyce <xref:System.ParamArrayAttribute> C# a v jazyce Visual Basic, které umožňuje explicitní použití zbytečné.  
  
<a name="Constructors"></a>
### <a name="constructors"></a>Konstruktory  
 Konstruktor je zvláštní druh metody, která vytváří nové instance třídy nebo struktury. Jako každá jiná metoda může konstruktor obsahovat parametry; konstruktory však nemají žádnou vrácenou `void`hodnotu (to znamená, že vrátí).  
  
 Pokud zdrojový kód pro třídu explicitně nedefinuje konstruktor, kompilátor obsahuje konstruktor bez parametrů. Pokud však zdrojový kód pro třídu definuje pouze parametrizované konstruktory, kompilátory jazyka a jazyka C# negenerují konstruktor bez parametrů.  
  
 Pokud zdrojový kód pro strukturu definuje konstruktory, musí být parametrizovány; struktura nemůže definovat konstruktor bez parametrů a kompilátory negenerují konstruktory bez parametrů pro struktury nebo jiné typy hodnot. Všechny typy hodnot mají implicitní konstruktor bez parametrů. Tento konstruktor je implementován běžným jazykem runtime a inicializuje všechna pole struktury na jejich výchozí hodnoty.  
  
<a name="Events"></a>
### <a name="events"></a>Akce  
 Událost definuje incident, na který lze odpovědět, a definuje metody pro přihlášení k odběru, odhlášení z odběru a vyvolání události. Události se často používají k informování jiných typů změn stavu. Další informace naleznete v tématu [Události](../../../docs/standard/events/index.md).  
  
<a name="NestedTypes"></a>
### <a name="nested-types"></a>Vnořené typy  
 Vnořený typ je typ, který je členem jiného typu. Vnořené typy by měly být pevně spojeny s jejich obsahující typ a nesmí být užitečné jako typ pro obecné účely. Vnořené typy jsou užitečné, když deklarující typ používá a vytváří instance vnořeného typu a použití vnořeného typu není vystaveno ve veřejných členech.  
  
 Vnořené typy jsou matoucí pro některé vývojáře a by neměly být veřejně viditelné, pokud existuje přesvědčivý důvod pro viditelnost. V dobře navržené knihovně by vývojáři měli zřídka používat vnořené typy k vytváření instancí objektů nebo deklarování proměnných.  

<a name="characteristics_of_type_members"></a>
## <a name="characteristics-of-type-members"></a>Charakteristika typových členů  
 Společný typový systém umožňuje členům typu mít různé vlastnosti; jazyky však nejsou nutné pro podporu všech těchto vlastností. Následující tabulka popisuje charakteristiky členů.  
  
|Charakteristika|Může se vztahovat na|Popis|  
|--------------------|------------------|-----------------|  
|abstract|Metody, vlastnosti a události|Typ neposkytuje implementaci metody. Typy, které dědí nebo implementují abstraktní metody, musí poskytnout implementaci metody. Jedinou výjimkou je, když odvozený typ je sám abstraktní typ. Všechny abstraktní metody jsou virtuální.|  
|soukromé, rodinné, montážní, rodinné a montážní, rodinné nebo|Všechny|Definuje přístupnost člena:<br /><br /> private<br /> Přístupné pouze ze stejného typu jako člen nebo v rámci vnořeného typu.<br /><br /> family<br /> Přístupné ze stejného typu jako člen a z odvozených typů, které dědí z něj.<br /><br /> sestavení<br /> Přístupné pouze v sestavě, ve kterém je definován typ.<br /><br /> rodina a montáž<br /> Přístupné pouze z typů, které mají nárok na přístup k rodině i sestavení.<br /><br /> rodina nebo montáž<br /> Přístupné pouze z typů, které mají nárok na přístup k rodině nebo sestavení.<br /><br /> public<br /> Přístupné z libovolného typu.|  
|finální|Metody, vlastnosti a události|Virtuální metodu nelze přepsat v odvozeném typu.|  
|inicializovat pouze|Fields (Pole)|Hodnotu lze pouze inicializovat a nelze ji zapsat po inicializaci.|  
|Instance|Pole, metody, vlastnosti a události|Pokud člen není označen `static` jako (C# a `Shared` C++), (Visual Basic), `virtual` (C# a C++) nebo `Overridable` (Visual Basic), je členem instance (neexistuje žádné klíčové slovo instance). V paměti bude tolik kopií těchto členů jako objekty, které je používají.|  
|literál|Fields (Pole)|Hodnota přiřazená poli je pevná hodnota předdefinovaného typu hodnoty známá v době kompilace. Pole literálu jsou někdy označovány jako konstanty.|  
|newslot nebo přepsat|Všechny|Definuje, jak člen interaguje s zděděnými členy, kteří mají stejný podpis:<br /><br /> diskusní server<br /> Skryje zděděné členy, kteří mají stejný podpis.<br /><br /> override<br /> Nahradí definici zděděné virtuální metody.<br /><br /> Výchozí hodnota je newslot.|  
|static|Pole, metody, vlastnosti a události|Člen patří k typu, na který je definován, nikoli do určité instance typu; člen existuje i v případě, že instance typu není vytvořena a je sdílena mezi všechny instance typu.|  
|virtual|Metody, vlastnosti a události|Metoda může být implementována odvozeným typem a může být vyvolána staticky nebo dynamicky. Pokud dynamické vyvolání se používá, typ instance, která provede volání za běhu (spíše než typ známý v době kompilace) určuje, která implementace metody je volána. Chcete-li vyvolat virtuální metodu staticky, proměnná může být přetypována na typ, který používá požadovanou verzi metody.|  
  
### <a name="overloading"></a>Přetížení  
 Každý člen typu má jedinečný podpis. Podpisy metody se skládají z názvu metody a seznamu parametrů (pořadí a typy argumentů metody). Více metod se stejným názvem lze definovat v rámci typu tak dlouho, dokud se jejich podpisy liší. Pokud jsou definovány dvě nebo více metod se stejným názvem, metoda se říká, že je přetížena. Například v <xref:System.Char?displayProperty=nameWithType>, <xref:System.Char.IsDigit%2A> metoda je přetížena. Jedna metoda <xref:System.Char>trvá . Druhá metoda trvá <xref:System.String> a <xref:System.Int32>.  
  
> [!NOTE]
> Návratový typ není považován za součást podpisu metody. To znamená, že metody nemohou být přetíženy, pokud se liší pouze podle návratového typu.  
  
### <a name="inheriting-overriding-and-hiding-members"></a>Dědění, přepsání a skrytí členů  
 Odvozený typ zdědí všechny členy svého základního typu; to znamená, že tyto členy jsou definovány na a k dispozici odvozený typ. Chování nebo vlastnosti zděděných členů lze upravit dvěma způsoby:  
  
- Odvozený typ může skrýt zděděný člen definováním nového člena se stejným podpisem. To může být provedeno, aby dříve veřejný člen soukromé nebo definovat nové `final`chování pro zděděné metody, která je označena jako .  
  
- Odvozený typ může přepsat zděděnou virtuální metodu. Přepsání metoda poskytuje novou definici metody, která bude vyvolána na základě typu hodnoty v době běhu, nikoli typ proměnné známé v době kompilace. Metoda může přepsat virtuální metodu pouze v případě, `final` že virtuální metoda není označena jako a nová metoda je alespoň stejně přístupná jako virtuální metoda.  
  
## <a name="see-also"></a>Viz také

- [Prohlížeč rozhraní API .NET](/dotnet/api)
- [CLR (Common Language Runtime)](../../../docs/standard/clr.md)
- [Převod typů v rozhraní .NET](../../../docs/standard/base-types/type-conversion.md)
