---
title: Obecný systém typů
description: Přečtěte si o systému typů v .NET.
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
ms.openlocfilehash: 5223c9b2031b1e25ec2f84326c811da1a78ddc15
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711412"
---
# <a name="common-type-system"></a>Obecný systém typů
Společný typ systému definuje, jak jsou typy deklarovány, používány a spravovány v modulu CLR (Common Language Runtime) a je také důležitou součástí podpory modulu runtime pro integraci mezi jazyky. Společný typ systému provádí následující funkce:  
  
- Vytvoří rozhraní, které pomáhá povolit integraci mezi jazyky, bezpečnost typů a vysoce výkonné provádění kódu.  
  
- Poskytuje objektově orientovaný model, který podporuje kompletní implementaci mnoha programovacích jazyků.  
  
- Definuje pravidla, která musí jazyky dodržovat, což pomáhá zajistit, aby objekty napsané v různých jazycích mohly vzájemně komunikovat.  
  
- Poskytuje knihovnu, která obsahuje primitivní datové typy (například <xref:System.Boolean>, <xref:System.Byte>, <xref:System.Char>, <xref:System.Int32>a <xref:System.UInt64>) používané při vývoji aplikací.  
  
 Toto téma obsahuje následující oddíly:  
  
- [Typy v rozhraní .NET](#types_in_the_net_framework)  
  
- [Definice typů](#type_definitions)  
  
- [Členy typu](#type_members)  
  
- [Charakteristiky členů typu](#characteristics_of_type_members)  
  
<a name="types_in_the_net_framework"></a>   
## <a name="types-in-net"></a>Typy v rozhraní .NET  
 Všechny typy v rozhraní .NET jsou buď typy hodnot nebo typy odkazů.  
  
 Typy hodnot jsou datové typy, jejichž objekty jsou reprezentovány skutečnou hodnotou daného objektu. Pokud je instance hodnotového typu přiřazena proměnné, je této proměnné předána nová kopie hodnoty.  
  
 Odkazové typy jsou datové typy, jejichž objekty jsou reprezentovány odkazem (podobně jako ukazatel) na skutečnou hodnotu objektu. Pokud je odkazový typ přiřazen proměnné, tato proměnná odkazuje (odkazuje na) na původní hodnotu. Není provedena žádná kopie.  
  
 Obecný systém typů v rozhraní .NET podporuje následující pět kategorií typů:  
  
- [Třídy](#Classes)  
  
- [Struktury](#Structures)  
  
- [Výčty](#Enumerations)  
  
- [Rozhraní](#Interfaces)  
  
- [Delegáti](#Delegates)  
  
<a name="Classes"></a>   
### <a name="classes"></a>Třídy  
 Třída je odkazový typ, který lze odvodit přímo z jiné třídy a implicitně odvozený z <xref:System.Object?displayProperty=nameWithType>. Třída definuje operace, které může objekt (což je instance třídy) provádět (metody, události nebo vlastnosti) a data, která objekt obsahuje (pole). I když třída obecně zahrnuje definice i implementaci (na rozdíl od rozhraní, například, která obsahuje pouze definici bez implementace), může mít jednoho nebo více členů, které nemají implementaci.  
  
 Následující tabulka popisuje některé vlastnosti, které třída může mít. Každý jazyk, který podporuje modul runtime, poskytuje způsob, jak označit, že třída nebo člen třídy má jednu nebo více těchto vlastností. Nicméně jednotlivé programovací jazyky, které cílí na rozhraní .NET, nemusí mít k dispozici všechny tyto vlastnosti.  
  
|Charakteristika|Popis|  
|--------------------|-----------------|  
|sealed|Určuje, že jinou třídu nelze z tohoto typu odvodit.|  
|implements|Označuje, že třída používá jedno nebo více rozhraní tím, že poskytuje implementace členů rozhraní.|  
|abstract|Označuje, že se nedá vytvořit instance třídy. Pokud ho chcete použít, musíte z něj odvodit jinou třídu.|  
|Dědí|Označuje, že instance třídy lze použít kdekoli je určena základní třída. Odvozená třída, která dědí ze základní třídy, může používat implementaci všech veřejných členů poskytovaných základní třídou nebo odvozenou třídu může přepsat implementaci veřejných členů s vlastní implementací.|  
|exportováno nebo neexportováno|Označuje, zda je třída viditelná vně sestavení, ve kterém je definována. Tato vlastnost se vztahuje pouze na třídy nejvyšší úrovně a nikoli na vnořené třídy.|  
  
> [!NOTE]
> Třída může být také vnořena do nadřazené třídy nebo struktury. Vnořené třídy mají také charakteristiky členů. Další informace naleznete v tématu [vnořené typy](#NestedTypes).  
  
 Členy třídy bez implementace jsou abstraktní členy. Třída, která má jednoho nebo více abstraktních členů, je sama o sobě abstraktní; Nelze vytvořit nové instance. Některé jazyky, které cílí na modul runtime, umožňují označit třídu jako abstraktní, a to i v případě, že žádný z jejích členů není abstraktní. Můžete použít abstraktní třídu, pokud chcete zapouzdřit základní sadu funkcí, které odvozené třídy mohou dědit nebo přepsat, pokud je to vhodné. Třídy, které nejsou abstraktní, jsou označovány jako konkrétní třídy.  
  
 Třída může implementovat libovolný počet rozhraní, ale může dědit z pouze jedné základní třídy kromě <xref:System.Object?displayProperty=nameWithType>, ze kterého všechny třídy dědí implicitní. Všechny třídy musí mít alespoň jeden konstruktor, který inicializuje nové instance třídy. Pokud konstruktor explicitně nedefinujete, většina kompilátorů automaticky nabídne konstruktor bez parametrů.  
  
<a name="Structures"></a>   
### <a name="structures"></a>Struktury  
 Struktura je hodnotový typ, který je odvozen implicitně z <xref:System.ValueType?displayProperty=nameWithType>, který je zase odvozen od <xref:System.Object?displayProperty=nameWithType>. Struktura je velmi užitečná pro reprezentace hodnot, jejichž požadavky na paměť jsou malé a pro předávání hodnot jako parametrů podle hodnot do metod, které mají parametry silného typu. V rozhraní .NET jsou definovány jako struktury všechny primitivní datové typy (<xref:System.Boolean>, <xref:System.Byte>, <xref:System.Char>, <xref:System.DateTime>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.UInt16>, <xref:System.UInt32>a <xref:System.UInt64>).  
  
 Podobně jako třídy struktury definují data (pole struktury) a operace, které mohou být provedeny na těchto datech (metody struktury). To znamená, že můžete volat metody ve strukturách, včetně virtuálních metod definovaných na <xref:System.Object?displayProperty=nameWithType> a <xref:System.ValueType?displayProperty=nameWithType>ch třídách, a jakékoli metody definované v samotném typu hodnoty. Jinými slovy struktury mohou mít pole, vlastnosti a události a také statické a nestatické metody. Můžete vytvářet instance struktur, předávat je jako parametry, ukládat je jako lokální proměnné nebo je ukládat v poli jiného typu hodnoty nebo odkazu. Struktury mohou také implementovat rozhraní.  
  
 Typy hodnot se také liší od tříd v několika ohledech. Nejdříve, i když implicitně dědí z <xref:System.ValueType?displayProperty=nameWithType>, nemohou přímo dědit z jakéhokoli typu. Podobně všechny typy hodnot jsou zapečetěné, což znamená, že z nich nemůže být odvozen žádný jiný typ. Nevyžadují také konstruktory.  
  
 Pro každý typ hodnoty modul CLR (Common Language Runtime) dodá odpovídající zabalený typ, což je třída, která má stejný stav a chování jako typ hodnoty. Instance typu hodnoty je zabalena, když je předána metodě, která přijímá parametr typu <xref:System.Object?displayProperty=nameWithType>. Je-li ovládací prvek vrácen z volání metody, které přijímá typ hodnoty jako parametr podle odkazu, není v krabici (tj. převeden z instance třídy zpět na instanci typu hodnoty). Některé jazyky vyžadují použití speciální syntaxe, pokud je požadován zabalený typ; ostatní v případě potřeby automaticky používají zabalený typ. Při definování typu hodnoty definujete jak zabalený, tak i nezabalený typ.  
  
<a name="Enumerations"></a>   
### <a name="enumerations"></a>Výčty  
 Výčet (Enum) je typ hodnoty, který dědí přímo z <xref:System.Enum?displayProperty=nameWithType> a který poskytuje alternativní názvy pro hodnoty základního primitivního typu. Typ výčtu má název, nadřízený typ, který musí být jedním z vestavěných nebo unsigned integerch typů (například <xref:System.Byte>, <xref:System.Int32>nebo <xref:System.UInt64>) a sadou polí. Pole jsou statické literální pole, z nichž každá představuje konstantu. Stejnou hodnotu lze přiřadit více polím. Pokud k tomu dojde, je nutné označit jednu z hodnot jako primární hodnotu výčtu pro reflexi a převod řetězce.  
  
 Můžete přiřadit hodnotu základního typu výčtu a naopak (modul runtime nevyžaduje žádné přetypování). Můžete vytvořit instanci výčtu a volat metody <xref:System.Enum?displayProperty=nameWithType>, jakož i jakékoli metody definované na základním typu výčtu. Některé jazyky však neumožňují předání výčtu jako parametru, pokud je vyžadována instance základního typu (nebo naopak).  
  
 Následující dodatečná omezení platí pro výčty:  
  
- Nemohou definovat své vlastní metody.  
  
- Nemohou implementovat rozhraní.  
  
- Nemohou definovat vlastnosti nebo události.  
  
- Nemohou být obecné, pokud nejsou obecné pouze proto, že jsou vnořené v rámci obecného typu. To znamená, že výčet nemůže mít vlastní parametry typu.  
  
    > [!NOTE]
    > Vnořené typy (včetně výčtů) vytvořené pomocí Visual Basic, C#a C++ zahrnují parametry typu všech nadřazených obecných typů a jsou proto Obecné i v případě, že nemají vlastní parametry typu. Další informace naleznete v tématu "vnořené typy" v tématu <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> reference.  
  
 Atribut <xref:System.FlagsAttribute> označuje speciální druh výčtu označovaný jako bitové pole. Samotný modul runtime nerozlišuje mezi tradičními výčty a bitovými poli, ale váš jazyk to může udělat. Po tomto rozlišení lze bitové operátory použít pro bitová pole, ale ne pro výčty, pro generování nepojmenovaných hodnot. Výčty se obecně používají pro seznamy jedinečných prvků, například dny v týdnu, názvy zemí nebo oblastí atd. Bitová pole jsou obecně používána pro seznamy kvality nebo množství, které mohou nastat v kombinaci, například `Red And Big And Fast`.  
  
 Následující příklad ukazuje, jak použít bitové pole i tradiční výčty.  
  
 [!code-csharp[Conceptual.Types.Enum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.enum/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Enum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.enum/vb/example.vb#1)]  
  
<a name="Interfaces"></a>   
### <a name="interfaces"></a>Rozhraní  
 Rozhraní definuje kontrakt, který určuje relaci "může provádět" nebo "má" relaci. Rozhraní se často používají k implementaci funkcí, jako je například porovnávání a třídění (rozhraní <xref:System.IComparable> a <xref:System.IComparable%601>), testování rovnosti (rozhraní <xref:System.IEquatable%601>) nebo výčet položek v kolekci (<xref:System.Collections.IEnumerable> a <xref:System.Collections.Generic.IEnumerable%601> rozhraní). Rozhraní mohou mít vlastnosti, metody a události, z nichž všechny jsou abstraktní členy; To znamená, že i když rozhraní definuje členy a jejich signatury, ponechá je typu, který implementuje rozhraní k definování funkcionality každého člena rozhraní. To znamená, že jakákoliv třída nebo struktura, která implementuje rozhraní, musí poskytovat definice abstraktních členů deklarovaných v rozhraní. Rozhraní může vyžadovat, aby jakákoli implementující třída nebo struktura také implementovala jedno nebo více jiných rozhraní.  
  
 Pro rozhraní platí následující omezení:  
  
- Rozhraní lze deklarovat s jakoukoli přístupností, ale členy rozhraní musí mít veřejnou přístupnost.  
  
- Rozhraní nemohou definovat konstruktory.  
  
- Rozhraní nemohou definovat pole.  
  
- Rozhraní mohou definovat pouze členy instance. Nemohou definovat statické členy.  
  
 Každý jazyk musí poskytovat pravidla pro mapování implementace na rozhraní, které vyžaduje člen, protože více než jedno rozhraní může deklarovat člena se stejnou signaturou a tito členové mohou mít samostatné implementace.  
  
<a name="Delegates"></a>   
### <a name="delegates"></a>Delegáti  
 Delegáti jsou odkazové typy, které slouží k podobnému účelu jako ukazatelé C++na funkci v. Používají se pro obslužné rutiny událostí a funkce zpětného volání v rozhraní .NET. Na rozdíl od ukazatelů na funkce jsou delegáti zabezpečeni, ověřitelné a typově bezpečné. Typ delegáta může představovat libovolnou metodu instance nebo statickou metodu, která má kompatibilní podpis.  
  
 Parametr delegáta je kompatibilní s odpovídajícím parametrem metody, pokud je typ parametru delegáta více omezující než typ parametru metody, protože to zaručuje, že argument předaný delegátovi lze bezpečně předat Metoda.  
  
 Podobně je návratový typ delegáta kompatibilní s návratovým typem metody, pokud návratový typ metody je více omezující než návratový typ delegáta, protože to zaručuje, že návratová hodnota metody může být bez obav přetypovat na návratový typ. e delegát.  
  
 Například delegát, který má parametr typu <xref:System.Collections.IEnumerable> a návratový typ <xref:System.Object> může představovat metodu, která má parametr typu <xref:System.Object> a návratovou hodnotu typu <xref:System.Collections.IEnumerable>. Další informace a příklady kódu naleznete v tématu <xref:System.Delegate.CreateDelegate%28System.Type%2CSystem.Object%2CSystem.Reflection.MethodInfo%29?displayProperty=nameWithType>.  
  
 Delegát je označován jako vázaný na metodu, kterou představuje. Kromě vazby k metodě může být delegát svázán s objektem. Objekt představuje první parametr metody a je předán metodě pokaždé, když je vyvolán delegát. Pokud je metoda metodou instance, je vázaný objekt předán jako implicitní parametr `this` (`Me` v Visual Basic); Pokud je metoda statická, objekt je předán jako první formální parametr metody a signatura delegáta musí odpovídat zbývajícím parametrům. Další informace a příklady kódu naleznete v tématu <xref:System.Delegate?displayProperty=nameWithType>.  
  
 Všichni delegáti dědí z <xref:System.MulticastDelegate?displayProperty=nameWithType>, které dědí z <xref:System.Delegate?displayProperty=nameWithType>. Jazyky C#, Visual Basic a C++ nepovolují dědění z těchto typů. Místo toho poskytují klíčová slova pro deklarování delegátů.  
  
 Vzhledem k tomu, že delegáti dědí z <xref:System.MulticastDelegate>, má delegát seznam vyvolání, což je seznam metod, které delegát představuje a které jsou spouštěny při vyvolání delegáta. Všechny metody v seznamu obdrží argumenty dodané při vyvolání delegáta.  
  
> [!NOTE]
> Návratová hodnota není definována pro delegáta, který má ve svém seznamu vyvolání více než jednu metodu, i když má delegát návratový typ.  
  
 V mnoha případech, jako je například metoda zpětného volání, představuje delegát pouze jednu metodu a jediné akce, které je třeba provést, vytvoří delegáta a vyvolá ho.  
  
 Pro delegáty, kteří představují více metod, poskytuje .NET metody <xref:System.Delegate> a <xref:System.MulticastDelegate> třídy delegátů pro podporu operací, jako je přidání metody do seznamu volání delegáta (metoda <xref:System.Delegate.Combine%2A?displayProperty=nameWithType>), odebrání metody (metoda <xref:System.Delegate.Remove%2A?displayProperty=nameWithType>) a získání seznamu vyvolání (metoda <xref:System.Delegate.GetInvocationList%2A?displayProperty=nameWithType>).  
  
> [!NOTE]
> Není nutné používat tyto metody pro delegáty obslužných rutin událostí v C#, C++a Visual Basic, protože tyto jazyky poskytují syntaxi pro přidávání a odebírání obslužných rutin událostí.  

<a name="type_definitions"></a>   
## <a name="type-definitions"></a>Definice typů  
 Definice typu zahrnuje následující:  
  
- Všechny atributy definované v typu.  
  
- Přístupnost typu (viditelnost).  
  
- Název typu.  
  
- Základní typ typu.  
  
- Jakákoli rozhraní implementovaná tímto typem.  
  
- Definice pro každý ze členů typu.  
  
### <a name="attributes"></a>Atributy  
 Atributy poskytují další uživatelsky definovaná metadata. Nejčastěji se používají k ukládání dalších informací o typu v jeho sestavení nebo k úpravě chování členu typu v době návrhu nebo prostředí run-time.  
  
 Atributy jsou samotné třídy, které dědí z <xref:System.Attribute?displayProperty=nameWithType>. Jazyky, které podporují použití atributů, mají vlastní syntaxi pro aplikování atributů na prvek jazyka. Atributy lze použít pro skoro libovolný prvek jazyka; konkrétní prvky, na které lze atribut použít, jsou definovány <xref:System.AttributeUsageAttribute>, který je použit pro tuto třídu atributu.  
  
### <a name="type-accessibility"></a>Přístupnost typu  
 Všechny typy mají modifikátor, který určuje přístupnost z jiných typů. Následující tabulka popisuje typ přístupnosti podporovaný modulem runtime.  
  
|Usnadnění|Popis|  
|-------------------|-----------------|  
|public,|Typ je přístupný pro všechna sestavení.|  
|sestavení|Typ je přístupný pouze v rámci jeho sestavení.|  
  
 Přístupnost vnořeného typu závisí na své doméně přístupnosti, která je určena deklarovanou přístupností člena a doménou přístupnosti bezprostředně obsahujícího typu. Nicméně doména přístupnosti vnořeného typu nemůže přesáhnout typ nadřazeného typu.  
  
 Doména přístupnosti vnořeného člena `M` deklarovaného v `T` typu v rámci programu `P` je definována takto (s označením, že `M` může být typ):  
  
- Pokud je deklarovaná přístupnost `M` `public`, doména přístupnosti `M` je doména přístupnosti `T`.  
  
- Pokud je deklarovaná přístupnost `M` `protected internal`, doména přístupnosti `M` je průnik domény přístupnosti `T` s textem programu `P` a textem programu libovolného typu odvozeného z `T` deklarovaného mimo `P`.  
  
- Pokud je deklarovaná přístupnost `M` `protected`, doména přístupnosti `M` je průnik domény přístupnosti `T` s textem programu `T` a jakýmkoli typem odvozeným od `T`.  
  
- Pokud je deklarovaná přístupnost `M` `internal`, doména přístupnosti `M` je průnik domény přístupnosti `T` s textem programu `P`.  
  
- Pokud je deklarovaná přístupnost `M` `private`, doména přístupnosti `M` je text programu `T`.  
  
### <a name="type-names"></a>Názvy typů  
 Společný typ systému ukládá pouze dvě omezení pro názvy:  
  
- Všechny názvy jsou kódované jako řetězce znaků Unicode (16 bitů).  
  
- U názvů nejsou povoleny hodnoty typu Embedded (16bitová) hodnota 0x0000.  
  
 Většina jazyků však zavádí další omezení pro názvy typů. Všechna porovnání jsou prováděna po bajtech, a proto jsou nezávislé na velikosti písmen a v národním prostředí.  
  
 I když typ může odkazovat na typy z jiných modulů a sestavení, musí být typ plně definovaný v jednom modulu .NET. (V závislosti na podpoře kompilátoru je však možné ji rozdělit do více souborů zdrojového kódu.) Názvy typů musí být jedinečné jenom v rámci oboru názvů. Aby bylo možné plně identifikovat typ, musí být název typu kvalifikován oborem názvů, který obsahuje implementaci typu.  
  
### <a name="base-types-and-interfaces"></a>Základní typy a rozhraní  
 Typ může dědit hodnoty a chování z jiného typu. Společný typ systému nepovoluje, aby typy dědily z více než jednoho základního typu.  
  
 Typ může implementovat libovolný počet rozhraní. Pro implementaci rozhraní musí typ implementovat všechny virtuální členy tohoto rozhraní. Virtuální metoda může být implementována odvozeným typem a lze ji vyvolat staticky nebo dynamicky.  

<a name="type_members"></a>   
## <a name="type-members"></a>Členy typu  
 Modul runtime umožňuje definovat členy typu, který určuje chování a stav typu. Mezi členy typu patří následující:  
  
- [Pole](#Fields)  
  
- [Vlastnosti](#Properties)  
  
- [Metody](#Methods)  
  
- [Konstruktory](#Constructors)  
  
- [Události](#Events)  
  
- [Vnořené typy](#NestedTypes)  
  
<a name="Fields"></a>   
### <a name="fields"></a>Pole  
 Pole popisuje a obsahuje část stavu typu. Pole mohou být libovolného typu podporovaného modulem runtime. Nejčastěji jsou pole buď `private`, nebo `protected`, aby byly přístupné pouze v rámci třídy nebo z odvozené třídy. Pokud hodnota pole může být upravena mimo jeho typ, je obvykle použito přistupující objekt sady vlastností. Veřejně vystavená pole jsou obvykle jen pro čtení a můžou mít dva typy:  
  
- Konstanty, jejichž hodnota je přiřazena v době návrhu. Jedná se o statické členy třídy, i když nejsou definovány pomocí klíčového slova `static` (`Shared` in Visual Basic).  
  
- Proměnné jen pro čtení, jejichž hodnoty lze přiřadit v konstruktoru třídy.  
  
 Následující příklad znázorňuje tato dvě použití polí jen pro čtení.  
  
 [!code-csharp[Conceptual.Types.Members.Fields#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.fields/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Fields#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.fields/vb/example.vb#1)]  
  
<a name="Properties"></a>   
### <a name="properties"></a>Vlastnosti  
 Vlastnost pojmenovává hodnotu nebo stav typu a definuje metody pro získání nebo nastavení hodnoty vlastnosti. Vlastnosti mohou být primitivní typy, kolekce primitivních typů, uživatelsky definované typy nebo kolekce uživatelsky definovaných typů. Vlastnosti jsou často používány k zachování veřejného rozhraní typu nezávisle na skutečném vyjádření typu. To umožňuje vlastnostem odrážet hodnoty, které nejsou přímo uloženy ve třídě (například když vlastnost vrátí vypočítanou hodnotu) nebo provést ověření před přiřazením hodnot k soukromým polím. Následující příklad znázorňuje druhý model.  
  
 [!code-csharp[Conceptual.Types.Members.Properties#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.properties/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Properties#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.properties/vb/example.vb#1)]  
  
 Kromě zahrnutí samotné vlastnosti obsahuje jazyk MSIL (Microsoft Intermediate Language) pro typ, který obsahuje čitelnou vlastnost, metodu `get_`*PropertyName* a jazyk MSIL pro typ, který obsahuje vlastnost s možností zápisu, obsahuje metodu `set_`*PropertyName* .  
  
<a name="Methods"></a>   
### <a name="methods"></a>Metody  
 Metoda popisuje operace, které jsou k dispozici na typu. Signatura metody specifikuje přípustné typy všech jeho parametrů a návratové hodnoty.  
  
 I když většina metod definuje přesný počet parametrů vyžadovaných pro volání metod, některé metody podporují proměnný počet parametrů. Výsledný deklarovaný parametr těchto metod je označen atributem <xref:System.ParamArrayAttribute>. Kompilátory jazyka obvykle poskytují klíčové slovo, například `params` v C# a `ParamArray` v Visual Basic, které umožňuje explicitní použití <xref:System.ParamArrayAttribute> zbytečných.  
  
<a name="Constructors"></a>   
### <a name="constructors"></a>Konstruktory  
 Konstruktor je speciální druh metody, který vytváří nové instance třídy nebo struktury. Stejně jako jakékoli jiné metody může konstruktor obsahovat parametry; konstruktory ale nemají žádnou návratovou hodnotu (to znamená, že vrací `void`).  
  
 Pokud zdrojový kód třídy explicitně nedefinuje konstruktor, kompilátor obsahuje konstruktor bez parametrů. Nicméně pokud zdrojový kód třídy definuje pouze parametrizované konstruktory, Visual Basic a C# kompilátory negenerují konstruktor bez parametrů.  
  
 Pokud zdrojový kód struktury definuje konstruktory, musí být parametrizované; Struktura nemůže definovat konstruktor bez parametrů a kompilátory negenerují konstruktory bez parametrů pro struktury a jiné typy hodnot. Všechny typy hodnot mají implicitní konstruktor bez parametrů. Tento konstruktor je implementován modulem CLR (Common Language Runtime) a inicializuje všechna pole struktury na jejich výchozí hodnoty.  
  
<a name="Events"></a>   
### <a name="events"></a>Události  
 Událost definuje incident, na který lze reagovat, a definuje metody pro odběr, zrušení odběru a vyvolání události. Události se často používají k informování dalších typů změn stavu. Další informace najdete v tématu [události](../../../docs/standard/events/index.md).  
  
<a name="NestedTypes"></a>   
### <a name="nested-types"></a>Vnořené typy  
 Vnořený typ je typ, který je členem nějakého jiného typu. Vnořené typy by měly být pevně spojeny s jejich nadřazeným typem a nesmí být užitečné jako typ obecného účelu. Vnořené typy jsou užitečné v případě, že deklarující typ používá a vytváří instance vnořeného typu a použití vnořeného typu není zveřejněno ve veřejných členech.  
  
 Vnořené typy jsou matoucí pro některé vývojáře a neměly by být veřejně viditelné, pokud neexistují přesvědčivé důvody pro přehlednost. V dobře navržené knihovně by vývojáři měli použít vnořené typy pouze zřídka pro vytvoření instance objektů nebo deklarování proměnných.  

<a name="characteristics_of_type_members"></a>   
## <a name="characteristics-of-type-members"></a>Charakteristiky členů typu  
 Společný typ systému umožňuje členům typu mít různé charakteristiky. jazyky však nejsou vyžadovány k podpoře všech těchto vlastností. Následující tabulka obsahuje popis vlastností členů.  
  
|Charakteristika|Může platit pro|Popis|  
|--------------------|------------------|-----------------|  
|abstract|Metody, vlastnosti a události|Typ neposkytuje implementaci metody. Typy, které dědí nebo implementují abstraktní metody, musí poskytovat implementaci pro metodu. Jediná výjimka je v případě, že odvozený typ je sám abstraktní typ. Všechny abstraktní metody jsou virtuální.|  
|privátní, Rodina, sestavení, rodina a sestavení, Rodina, sestavení nebo veřejné|Všechny|Definuje přístupnost člena:<br /><br /> private<br /> Přístupný pouze v rámci stejného typu jako člen nebo v rámci vnořeného typu.<br /><br /> rodina<br /> Přístupné ze stejného typu jako člen a z odvozeného typu, který z něj dědí.<br /><br /> sestavení<br /> Přístupný pouze v sestavení, ve kterém je definován typ.<br /><br /> Rodina a sestavení<br /> Přístupný pouze z typů, které jsou způsobilé pro rodinu a přístup k sestavení.<br /><br /> řada nebo sestavení<br /> Přístupný pouze z typů, které jsou způsobilé pro přístup buď k rodině, nebo k sestavení.<br /><br /> public,<br /> Přístupný z libovolného typu.|  
|finální|Metody, vlastnosti a události|Virtuální metodu nelze přepsat v odvozeném typu.|  
|pouze pro inicializaci|Pole|Hodnotu lze inicializovat pouze a nelze ji zapsat po inicializaci.|  
|instance|Pole, metody, vlastnosti a události|Pokud člen není označen jako `static`C# (a C++), `Shared` (Visual Basic), `virtual` (C# a C++) nebo `Overridable` (Visual Basic), jedná se o člen instance (neexistuje žádné klíčové slovo instance). V paměti bude tolik kopií takových členů, jako jsou objekty, které ho používají.|  
|literál|Pole|Hodnota přiřazená k poli je pevná hodnota, která je známá v době kompilace předdefinovaného typu hodnoty. Pole literálu jsou někdy označována jako konstanty.|  
|NewSlot nebo override|Všechny|Definuje, jak člen komunikuje se zděděnými členy, které mají stejnou signaturu:<br /><br /> NewSlot<br /> Skryje zděděné členy, které mají stejnou signaturu.<br /><br /> přepsání<br /> Nahrazuje definici zděděné virtuální metody.<br /><br /> Výchozí hodnota je NewSlot.|  
|static|Pole, metody, vlastnosti a události|Člen patří do typu, ve kterém je definován, nikoli na konkrétní instanci typu; člen existuje i v případě, že instance typu není vytvořena a je sdílena mezi všemi instancemi typu.|  
|virtual|Metody, vlastnosti a události|Metoda může být implementována odvozeným typem a lze ji vyvolat staticky nebo dynamicky. Pokud se používá dynamické volání, typ instance, která provádí volání v době běhu (spíše než typ známý v době kompilace), určuje, která implementace metody je volána. Chcete-li vyvolat virtuální metodu staticky, proměnná může být převedena na typ, který používá požadovanou verzi metody.|  
  
### <a name="overloading"></a>Přetížení  
 Každý člen typu má jedinečný podpis. Signatury metody se skládají z názvu metody a seznamu parametrů (pořadí a typy argumentů metody). V rámci typu lze definovat více metod se stejným názvem, pokud se jejich signatury liší. Pokud jsou definovány dvě nebo více metod se stejným názvem, je metoda označována jako přetížená. Například v <xref:System.Char?displayProperty=nameWithType>je metoda <xref:System.Char.IsDigit%2A> přetížena. Jedna z metod používá <xref:System.Char>. Druhá metoda přebírá <xref:System.String> a <xref:System.Int32>.  
  
> [!NOTE]
> Návratový typ není považován za součást signatury metody. To znamená, že metody nemohou být přetíženy, pokud se liší pouze návratovým typem.  
  
### <a name="inheriting-overriding-and-hiding-members"></a>Dědění, přepisování a skrývání členů  
 Odvozený typ dědí všechny členy svého základního typu; To znamená, že tyto členy jsou definovány v a jsou k dispozici pro odvozený typ. Chování nebo vlastnosti zděděných členů lze upravit dvěma způsoby:  
  
- Odvozený typ může skrýt zděděného člena definováním nového člena se stejnou signaturou. To může být provedeno pro vytvoření privátního veřejného člena nebo pro definování nového chování pro zděděnou metodu, která je označena jako `final`.  
  
- Odvozený typ může přepsat zděděnou virtuální metodu. Přepisování metody poskytuje novou definici metody, která bude vyvolána na základě typu hodnoty v době běhu, nikoli typu proměnné známé v době kompilace. Metoda může přepsat virtuální metodu pouze v případě, že virtuální metoda není označena jako `final` a nová metoda je přinejmenším dostupná jako virtuální metoda.  
  
## <a name="see-also"></a>Viz také:

- [Prohlížeč rozhraní API .NET](/dotnet/api)
- [Modul CLR (Common Language Runtime)](../../../docs/standard/clr.md)
- [Převod typů v rozhraní .NET](../../../docs/standard/base-types/type-conversion.md)
