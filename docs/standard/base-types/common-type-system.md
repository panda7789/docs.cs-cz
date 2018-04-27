---
title: Obecný systém typů
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 25
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4660e8764c429f526e05e8e7b6c44bd30c4172c1
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="common-type-system"></a>Obecný systém typů
Obecný systém typů definuje, jak jsou typy deklarovat, použít a spravovat v modulu common language runtime který je taky důležitou součástí modulu runtime podporu integrace mezi jazyky. Obecný systém typů provádí následující funkce:  
  
-   Vytvoří rozhraní, které pomáhá povolení integrace mezi jazyky, bezpečnost typů a provádění kódu vysoce výkonné.  
  
-   Poskytuje objektově orientovaný model, který podporuje úplnou implementaci řadě programovacích jazyků.  
  
-   Definuje pravidla, které musí postupovat podle jazyky, což pomůže zajistit, že objekty, které jsou napsané v různých jazycích může dojít ke vzájemné interakci.  
  
-   Poskytuje knihovnu, která obsahuje primitivní datové typy (například <xref:System.Boolean>, <xref:System.Byte>, <xref:System.Char>, <xref:System.Int32>, a <xref:System.UInt64>) používané při vývoji aplikace.  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Typy v rozhraní .NET](#types_in_the_net_framework)  
  
-   [Definice typů](#type_definitions)  
  
-   [Členy typu](#type_members)  
  
-   [Charakteristika členy typu](#characteristics_of_type_members)  
  
<a name="types_in_the_net_framework"></a>   
## <a name="types-in-net"></a>Typy v rozhraní .NET  
 Všechny typy v rozhraní .NET jsou buď hodnotové nebo odkazové typy.  
  
 Typy hodnot jsou datové typy, jejichž objekty jsou reprezentované pomocí objektu skutečnou hodnotu. Pokud instance typu hodnota je přiřazený k proměnné, tuto proměnnou dostane novou kopii hodnoty.  
  
 Odkazové typy jsou datové typy, jejichž objekty jsou reprezentované pomocí odkaz (podobně jako ukazatel) na skutečnou hodnotu objektu. Pokud typ odkazu je přiřazený k proměnné, tuto proměnnou odkazuje (směřuje) původní hodnotu. Je vytvořena žádná kopie.  
  
 Obecný systém typů v rozhraní .NET podporuje následujících pět kategorií typů:  
  
-   [Třídy](#Classes)  
  
-   [Struktury](#Structures)  
  
-   [Výčty](#Enumerations)  
  
-   [Rozhraní](#Interfaces)  
  
-   [Delegáti](#Delegates)  
  
<a name="Classes"></a>   
### <a name="classes"></a>Třídy  
 Třída je typu odkazu, který lze odvodit přímo z jiné třídy, a je implicitně odvozena z <xref:System.Object?displayProperty=nameWithType>. Třída definuje operace, že objekt (což je instance třídy) může provádět (metody, události nebo vlastnosti) a data, že objekt obsahuje (pole). I když třídu obvykle obsahuje definice a implementaci (na rozdíl od rozhraní, například, které obsahují pouze definici bez implementace), může mít jeden nebo více členů, které nemají implementaci.  
  
 Následující tabulka popisuje některé charakteristiky, které mohou mít třídu. Každý jazyk, který podporuje modul runtime poskytuje způsob, jak označuje, že třída nebo člen třídy obsahuje jeden nebo více z těchto vlastností. Ale jednotlivé programovací jazyky cílených .NET nemusí mít tyto charakteristiky k dispozici.  
  
|Vlastnosti|Popis|  
|--------------------|-----------------|  
|sealed|Určuje, že z tohoto typu nelze odvodit jiné třídy.|  
|implements|Označuje, že třída používá jedno nebo více rozhraní tím, že poskytuje implementace členů rozhraní.|  
|abstract|Označuje, že nelze vytvořit instanci třídy. Pokud chcete použít, musí být jiné třídy z něj.|  
|dědí|Označuje, že instance této třídy lze použít všude, kde je zadán základní třídy. Odvozené třídy, která dědí z databáze třídu, můžete použít implementace všechny veřejné členy poskytuje základní třídu nebo odvozené třídy můžete přepsat implementace veřejné členy vlastní implementací.|  
|Export nebo není exportovat|Určuje, zda je třída viditelné mimo sestavení, ve kterém je definovaný. Tato vlastnost se týká pouze na nejvyšší úrovni třídy a vnořené třídy.|  
  
> [!NOTE]
>  Třídy mohou být také vnořené v nadřazené třídě nebo struktuře. Vnořené třídy také mít vlastnosti člena. Další informace najdete v tématu [vnořené typy](#NestedTypes).  
  
 Členy třídy, které nemají implementaci jsou abstraktní členy. Třída, která má jeden nebo více abstraktní členy je sám abstraktní; Nelze vytvořit novou instanci. Některé jazyky, které používají modul runtime umožňuje označit jako abstraktní třídu, i v případě, že žádný z jejích členů není abstraktní. Abstraktní třídu můžete použít, pokud chcete zapouzdřit základní sadu funkcí, které odvozených třídách můžete dědit nebo případě potřeby přepsat. Třídy, které nejsou abstraktní jsou označovány jako konkrétní třídy.  
  
 Třída může implementovat libovolný počet rozhraní, ale může dědit vlastnosti pouze z jediné základní třídy kromě <xref:System.Object?displayProperty=nameWithType>, z všechny třídy dědí implicitně. Všechny třídy musí mít alespoň jeden konstruktor, který inicializuje nové instance třídy. Pokud konstruktor nejsou explicitně definovány, většina kompilátory automaticky poskytne výchozí konstruktor (bez parametrů).  
  
<a name="Structures"></a>   
### <a name="structures"></a>Struktury  
 Struktura je hodnota typ, který je implicitně odvozena z <xref:System.ValueType?displayProperty=nameWithType>, který je zase odvozen z <xref:System.Object?displayProperty=nameWithType>. Struktura je velmi užitečná pro představující hodnoty jsou malé požadavky na paměť a předání hodnoty jako parametry-hodnota metody, které mají parametry silného typu. V rozhraní .NET, všechny primitivní datové typy (<xref:System.Boolean>, <xref:System.Byte>, <xref:System.Char>, <xref:System.DateTime>, <xref:System.Decimal>, <xref:System.Double>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.SByte>, <xref:System.Single>, <xref:System.UInt16>, <xref:System.UInt32>, a <xref:System.UInt64>) jsou definovány jako struktury.  
  
 Stejně jako třídy struktury definovat dat (pole struktury) a operace, které lze provést na data (metody struktury). To znamená, že můžete volat metody pro struktury, včetně virtuální metody definované na <xref:System.Object?displayProperty=nameWithType> a <xref:System.ValueType?displayProperty=nameWithType> třídy a jakékoli metody definované na typ hodnoty sám sebe. Jinými slovy struktury může mít pole, vlastnosti a události, jakož i statické a nestatické metody. Můžete vytvořit instance struktury, je předat jako parametry, uložit je jako místní proměnné, nebo uložit je do pole jiný typ hodnoty nebo typ odkazu. Struktury můžete taky implementovat rozhraní.  
  
 Typy hodnot také z tříd v několika ohledech liší. První, i když implicitně dědí z <xref:System.ValueType?displayProperty=nameWithType>, nemohou přímo dědit z libovolného typu. Podobně, jako jsou zapečetěné všechny typy hodnot, což znamená, že žádný jiný typ lze odvodit z nich. Také nevyžadují konstruktory.  
  
 Pro každý typ hodnoty poskytuje modul common language runtime odpovídající zabalený typ, což je třída, která má stejné chování jako typ hodnoty a stavu. Instance typu hodnota je zabalená, když je předán do metodu, která přijímá parametr typu <xref:System.Object?displayProperty=nameWithType>. Nezabalený (to znamená, převést z instance třídy zpět na instanci typu hodnoty) při vrácení řízení z volání metody, která přijímá typ hodnoty jako parametr odkazem. Některé jazyky vyžadují použití speciální syntaxe, pokud je potřeba; zabalený typ. pevně určené typ ostatní automaticky používat, pokud je to potřeba. Když definujete typ hodnoty, definujete zabalený i nezabalený typu.  
  
<a name="Enumerations"></a>   
### <a name="enumerations"></a>Výčty  
 Výčet (výčtu) je typ hodnoty, který dědí přímo z <xref:System.Enum?displayProperty=nameWithType> a že zdroje alternativní názvy pro hodnoty základní primitivního typu. Typ výčtu, má název, základní typ, který musí být jeden z typů předdefinované podepsaný držitelem nebo bez znaménka celé číslo (například <xref:System.Byte>, <xref:System.Int32>, nebo <xref:System.UInt64>) a sady polí. Pole jsou statických polí literálu, z nichž každý představuje konstantu. Stejnou hodnotu lze přiřadit k více polí. V takovém případě je třeba jedna z hodnot označit jako primární hodnotu výčtu pro reflexe a převod řetězce.  
  
 Můžete přiřadit hodnotu základní typ výčtu a naopak (žádné přetypování vyžadují modul runtime). Můžete vytvořit instanci výčtu a volat metody <xref:System.Enum?displayProperty=nameWithType>, stejně jako jakékoli metody definované u základního typu výčtu. Ale některé jazyky pravděpodobně neumožní předat výčet jako parametr, pokud je nutné použít instanci základní typ (nebo naopak).  
  
 Pro výčty platí následující omezení:  
  
-   Nemohou definovat vlastní metody.  
  
-   Nemohou implementovat rozhraní.  
  
-   Nemohou definovat vlastnosti nebo události.  
  
-   Nemohou být obecné, pokud nejsou obecné pouze vzhledem k tomu, že jsou vnořené do obecného typu. To znamená výčet nemůže mít parametry typu své vlastní.  
  
    > [!NOTE]
    >  Vnořené typy (včetně výčty) jsou vytvořené pomocí jazyka Visual Basic, C# a C++ zahrnují parametry typu všech nadřazených obecných typů a jsou tedy Obecné, i když nemají vlastní parametry typu. Další informace najdete v části "Vnořené typy" v <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> referenční téma.  
  
 <xref:System.FlagsAttribute> Atribut označuje zvláštní druh výčtu nazývaný bitové pole. Samotný modul runtime nerozlišuje mezi tradiční výčty a bitová pole, ale váš jazyk může udělat. Když se rozlišují, bitové operátory lze na bitová pole, ale ne na výčty, generování nepojmenované hodnot. Výčty jsou obvykle používány k seznam jedinečných prvky, jako jsou například dny v týdnu, země nebo oblasti názvy a tak dále. Bitová pole jsou obecně používány k seznamy vlastností nebo množství, které můžou nastat v kombinaci, jako například `Red And Big And Fast`.  
  
 Následující příklad ukazuje způsob použití bitových polí a tradiční výčty.  
  
 [!code-csharp[Conceptual.Types.Enum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.enum/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Enum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.enum/vb/example.vb#1)]  
  
<a name="Interfaces"></a>   
### <a name="interfaces"></a>Rozhraní  
 Rozhraní definuje kontrakt, který určuje vztah "provést" nebo "má" relace. Rozhraní se často používají k implementaci funkcí, jako je například porovnávání a řazení ( <xref:System.IComparable> a <xref:System.IComparable%601> rozhraní), testování rovnosti ( <xref:System.IEquatable%601> rozhraní), nebo vytváření výčtu položky v kolekci ( <xref:System.Collections.IEnumerable> a <xref:System.Collections.Generic.IEnumerable%601> rozhraní). Rozhraní může mít vlastnosti, metod a události, které jsou abstraktní členy; To znamená i když rozhraní definuje členy a jejich podpisy, zůstanou ho typu, který implementuje rozhraní definovat funkci u každého člena rozhraní. To znamená, že všechny třídu nebo strukturu, která implementuje rozhraní musí poskytnout definici pro abstraktní členy deklarované v rozhraní. Rozhraní může vyžadovat žádné implementující třídu nebo strukturu také implementovat jednu nebo více rozhraní.  
  
 Rozhraní se vztahují následující omezení:  
  
-   Rozhraní lze deklarovat s žádné usnadnění, ale všechny členy rozhraní musí mít veřejnou dostupnost.  
  
-   Rozhraní nelze definovat konstruktory.  
  
-   Rozhraní nelze definovat pole.  
  
-   Rozhraní můžete definovat jenom členy instancí. Nemohou definovat statické členy.  
  
 Jednotlivé jazyky nutné zadat pravidla pro mapování implementace rozhraní, která vyžaduje člena, protože víc než jedno rozhraní můžou deklarovat člen se stejným podpisem a tito členové můžou mít samostatné implementace.  
  
<a name="Delegates"></a>   
### <a name="delegates"></a>Delegáty  
 Delegáti jsou odkazové typy, které mají účely podobná ukazatelů na funkce v jazyce C++. Používají se pro obslužné rutiny událostí a funkce zpětného volání v rozhraní .NET. Na rozdíl od ukazatelů na funkce Delegáti jsou zabezpečené, ověřit a zadejte bezpečné. Typem delegáta může představovat libovolnou metodu instance nebo statickou metodu, která má kompatibilní podpis.  
  
 Parametr delegáta je kompatibilní s odpovídajícího parametru metody, pokud je typ parametru delegáta více omezující než typ parametru metody, protože to zaručuje, že argument předaný delegát můžete předat bezpečně Metoda.  
  
 Návratový typ delegáta je podobně kompatibilní s návratovým typem metody, pokud je návratový typ metody více omezující než návratový typ delegáta, protože to zaručuje, že návratová hodnota metody můžete bezpečně přetypovat na návratový typ e delegáta.  
  
 Například delegáta, který má parametr typu <xref:System.Collections.IEnumerable> a návratový typ <xref:System.Object> může představovat metodu, která má parametr typu <xref:System.Object> a návratovou hodnotu typu <xref:System.Collections.IEnumerable>. Další informace a ukázkový kód, najdete v části <xref:System.Delegate.CreateDelegate%28System.Type%2CSystem.Object%2CSystem.Reflection.MethodInfo%29?displayProperty=nameWithType>.  
  
 Delegát je označován bylo vázané na metodu, kterou představuje. Kromě vázaná metodu delegáta může být vázána na objekt. Objekt představuje první parametr metody a je předaný metodě pokaždé, když je vyvolán delegát. Pokud je metoda metody instance, vázaný objekt je předán jako implicitní `this` parametr (`Me` v jazyce Visual Basic); Pokud metoda je statická, objekt je předán jako první formální parametr metody a delegáta musí odpovídat zbývající parametry. Další informace a ukázkový kód, najdete v části <xref:System.Delegate?displayProperty=nameWithType>.  
  
 Všechny delegáti dědí z <xref:System.MulticastDelegate?displayProperty=nameWithType>, který dědí z <xref:System.Delegate?displayProperty=nameWithType>. Jazyk C#, Visual Basic a C++ neumožňují dědičnost z těchto typů. Místo toho poskytují klíčová slova pro deklarování delegáti.  
  
 Protože delegáti dědí z <xref:System.MulticastDelegate>, delegát má seznam vyvolání, což je seznam metod, které představuje delegáta a které jsou spouštěny při vyvolání delegáta. Všechny metody v seznamu zobrazí zadané argumenty při vyvolání delegáta.  
  
> [!NOTE]
>  Návratová hodnota není definován pro delegáta, který má více než jednu metodu ve svém seznamu volání i v případě, že má návratový typ delegáta.  
  
 V mnoha případech, jako je zpětné volání metod, delegát představuje pouze jednu metodu a pouze akce, které je třeba provést jsou vytváření delegáta a vyvolání ho.  
  
 Pro delegáti, které představují několik metod, .NET poskytuje metody <xref:System.Delegate> a <xref:System.MulticastDelegate> delegovat třídy pro podporu operací, jako je například přidání metody do seznamu vyvolání tohoto delegáta ( <xref:System.Delegate.Combine%2A?displayProperty=nameWithType> metoda), odebrání metody ( <xref:System.Delegate.Remove%2A?displayProperty=nameWithType> metoda) a získání seznamu vyvolání ( <xref:System.Delegate.GetInvocationList%2A?displayProperty=nameWithType> metoda).  
  
> [!NOTE]
>  Není potřeba použít tyto metody pro delegátů obslužných rutin událostí v jazyce C#, C++ a Visual Basic, protože tyto jazyky poskytují syntaxi pro přidávání a odebírání obslužných rutin událostí.  
  
 
  
<a name="type_definitions"></a>   
## <a name="type-definitions"></a>Definice typů  
 Definice typu zahrnuje následující položky:  
  
-   Všechny atributy definovanou u typu.  
  
-   Přístupnost typu (přehled).  
  
-   Název typu.  
  
-   Základní typ tohoto typu.  
  
-   Žádné rozhraní implementované typu.  
  
-   Definice pro každý z členů tohoto typu.  
  
### <a name="attributes"></a>Atributy  
 Atributy poskytují další metadata definovaná uživatelem. Nejčastěji se používají k ukládání Další informace o typu v jeho sestavení nebo chcete změnit chování člena typu buď návrhu nebo běhové prostředí.  
  
 Atributy jsou samotné třídy, které dědí od <xref:System.Attribute?displayProperty=nameWithType>. Jazyky, které podporují použití atributů mají své vlastní syntaxe pro použití atributů do elementu jazyk. Atributy lze použít jako prakticky libovolný element jazyka. konkrétní elementy, na které můžete použít atribut jsou definované <xref:System.AttributeUsageAttribute> který se použije pro danou třídu atributů.  
  
### <a name="type-accessibility"></a>Typ usnadnění  
 Všechny typy mají modifikátor, který řídí jejich usnadnění od ostatních typů. Následující tabulka popisuje přístupnosti typu podporovaná modulem runtime.  
  
|Usnadnění|Popis|  
|-------------------|-----------------|  
|public|Typ je přístupný pro všechny sestavení.|  
|sestavení|Typ je přístupné pouze v rámci jeho sestavení.|  
  
 Usnadnění vnořeného typu závisí na jeho doména přístupnosti, což je dáno tím deklarované usnadnění člena a doména přístupnosti okamžitě nadřazeného typu. Doména přístupnosti vnořeného typu však nesmí překročit u nadřazeného typu.  
  
 Doména přístupnosti vnořeného člena `M` deklarovaného v typu `T` v rámci programu `P` je definován následujícím způsobem (který poznamenat `M` může být sám typ):  
  
-   Pokud je deklarovaná přístupnost člena `M` je `public`, doména přístupnosti `M` je doména přístupnosti `T`.  
  
-   Pokud je deklarovaná přístupnost člena `M` je `protected internal`, doména přístupnosti `M` je průnik doména přístupnosti `T` s textem programu `P` a textem programu jakýkoli typ odvozený z `T` deklarovaný mimo `P`.  
  
-   Pokud je deklarovaná přístupnost člena `M` je `protected`, doména přístupnosti `M` je průnik doména přístupnosti `T` s textem programu `T` a jakéhokoli typu odvozeného z `T`.  
  
-   Pokud je deklarovaná přístupnost člena `M` je `internal`, doména přístupnosti `M` je průnik doména přístupnosti `T` s textem programu `P`.  
  
-   Pokud je deklarovaná přístupnost člena `M` je `private`, doména přístupnosti `M` je text programu `T`.  
  
### <a name="type-names"></a>Názvy typů  
 Obecný systém typů vynucuje pouze dvě omezení na názvy:  
  
-   Všechny názvy jsou zakódovány jako řetězce znaků Unicode (16 bitů).  
  
-   Názvy nejsou povolené tak, aby měl hodnotu embedded (16 bitů) 0x0000.  
  
 Většina jazyků však zavádí další omezení pro názvy typů. Všechny porovnání se provádí na základě bajtové byte a proto jsou velká a malá písmena a nezávislé na národním prostředí.  
  
 I když typu může odkazové typy z jiných moduly a sestavení, musí být typu plně definována v rámci jednoho modulu .NET. (V závislosti na podpoře kompilátoru však ho lze rozdělit do několika soubory zdrojového kódu.) Názvy typů musí být jedinečný pouze v rámci oboru názvů. Pokud chcete plně identifikovat typu, musí být kvalifikovaný název typu obor názvů, který obsahuje implementaci typu.  
  
### <a name="base-types-and-interfaces"></a>Základní typy a rozhraní  
 Typ může dědit vlastnosti hodnoty a chování z jiného typu. Obecný systém typů nepovoluje typy dědění z více než jeden základního typu.  
  
 Typ můžete implementovat libovolný počet rozhraní. Pokud chcete implementovat rozhraní, musí typ implementovat virtuální členy rozhraní. Virtuální metoda může být implementováno odvozeným typem a vyvolána staticky nebo dynamicky.  
  
  
  
<a name="type_members"></a>   
## <a name="type-members"></a>Členy typu  
 Modul runtime umožňuje definovat členy vaší typu, který určuje chování a stav tohoto typu. Členy typu zahrnují následující:  
  
-   [Pole](#Fields)  
  
-   [Vlastnosti](#Properties)  
  
-   [Metody](#Methods)  
  
-   [Konstruktory](#Constructors)  
  
-   [Události](#Events)  
  
-   [Vnořené typy](#NestedTypes)  
  
<a name="Fields"></a>   
### <a name="fields"></a>Pole  
 Pole popisuje a obsahuje část stavu typu. Pole můžou být jakéhokoli typu podporovaná modulem runtime. Nejčastěji, jsou pole buď `private` nebo `protected`, takže budou přístupné pouze v rámci třídy nebo z odvozené třídy. Pokud hodnotu pole může být změněna mimo její typ, použije se obvykle vlastnosti. Veřejně vystavené položky jsou obvykle jen pro čtení a může mít dva typy:  
  
-   Konstanty, jehož hodnota je přiřazena v době návrhu. Tyto jsou statické členy třídy, i když nejsou definovány pomocí `static` (`Shared` v jazyce Visual Basic) – klíčové slovo.  
  
-   Jen pro čtení proměnné, jejichž hodnoty lze přiřadit v konstruktoru třídy.  
  
 Následující příklad znázorňuje tyto dvě použití pole jen pro čtení.  
  
 [!code-csharp[Conceptual.Types.Members.Fields#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.fields/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Fields#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.fields/vb/example.vb#1)]  
  
<a name="Properties"></a>   
### <a name="properties"></a>Vlastnosti  
 Vlastnost názvy hodnota nebo stavu typu a definuje metody pro získání nebo nastavení hodnoty vlastnosti. Vlastnosti mohou být primitivní typy, kolekce primitivní typy, uživatelem definované typy nebo kolekce uživatelem definované typy. Vlastnosti se často používají k udržování nezávislé veřejné rozhraní typu z tohoto typu skutečný. To umožňuje vlastnosti tak, aby odrážela hodnoty, které nejsou přímo uložené ve třídě (například když vlastnost vrací vypočtenou hodnotou) nebo provést ověření, než k privátním polím přiřazené hodnoty. Následující příklad znázorňuje druhý případ.  
  
 [!code-csharp[Conceptual.Types.Members.Properties#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.types.members.properties/cs/example.cs#1)]
 [!code-vb[Conceptual.Types.Members.Properties#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.types.members.properties/vb/example.vb#1)]  
  
 Kromě samotné vlastnosti, včetně Microsoft (MSIL intermediate language) pro typ, který obsahuje čitelnou vlastnost zahrnuje `get_` *propertyname* metoda a MSIL pro typ, který obsahuje možností zápisu obsahuje vlastnost `set_` *propertyname* metoda.  
  
<a name="Methods"></a>   
### <a name="methods"></a>Metody  
 Metoda popisuje operace, které jsou k dispozici u typu. Metoda podpis určuje povolené typy všechny jeho parametrů a hodnoty.  
  
 I když většina metody definovat přesné počet parametrů požadovaných pro volání metod, některé metody podporují proměnný počet parametrů. Výsledný deklarovaný parametr těchto metod je označené jako <xref:System.ParamArrayAttribute> atribut. Kompilátory jazyka obvykle poskytují klíčového slova, například `params` v jazyce C# a `ParamArray` v jazyce Visual Basic, který zpřístupňuje explicitní použití <xref:System.ParamArrayAttribute> zbytečné.  
  
<a name="Constructors"></a>   
### <a name="constructors"></a>Konstruktory  
 Konstruktor je zvláštní druh metodu, která vytvoří nové instance třídy třídu nebo strukturu. Podobně jako jakékoli jiné metody konstruktor může obsahovat parametry; ale konstruktory nemají žádnou návratovou hodnotu (to znamená, že budou vracet `void`).  
  
 Pokud zdrojový kód pro třídu explicitně nedefinuje konstruktor, kompilátor obsahuje výchozí konstruktor (bez parametrů). Ale pokud zdrojový kód pro třídu definuje pouze parametrizované konstruktory, kompilátory jazyka Visual Basic a C# negenerují konstruktor bez parametrů.  
  
 Pokud zdrojový kód pro strukturu definuje konstruktory, musí být parametry; struktura nemůže definovat výchozí konstruktor (bez parametrů) a negenerují bezparametrové konstruktory struktury nebo jiné typy hodnot. Všechny typy hodnot mají implicitní výchozí konstruktor. Tento konstruktor je implementováno modulem modul common language runtime a inicializuje všechna pole na výchozí hodnoty strukturu.  
  
<a name="Events"></a>   
### <a name="events"></a>Události  
 Událost definuje incident, který může být odpověděl a definuje metody pro přihlášení k odběru, Odhlašujete a vyvolá událost. Události se často používají k informování jiné typy změny stavu. Další informace najdete v tématu [události](../../../docs/standard/events/index.md).  
  
<a name="NestedTypes"></a>   
### <a name="nested-types"></a>Vnořené typy  
 Vnořené typ je typ, který je členem některé jiné typy. Vnořené typy by měla být úzce spojeny s jejich obsahující typ a nesmí být užitečné jako typ pro obecné účely. Vnořené typy jsou užitečné, když deklarující typ používá a vytváří instance vnořené typy a použití vnořených typu není viditelné ve veřejné členy.  
  
 Vnořené typy jsou pro někteří vývojáři matoucí a nesmí být veřejně viditelný, pokud nejsou přesvědčivý důvod pro viditelnosti. V knihovně dobře navrženou by vývojáři obvykle nemusí použít vnořené typy pro vytvoření instancí objektů nebo deklarujte proměnné.  
  
  
  
<a name="characteristics_of_type_members"></a>   
## <a name="characteristics-of-type-members"></a>Charakteristika členy typu  
 Obecný systém typů umožňuje členům typu mít různé vlastnosti; jazyky však nemusí podporovat všechny tyto vlastnosti. Následující tabulka popisuje vlastnosti členů.  
  
|Vlastnosti|Můžete použít pro|Popis|  
|--------------------|------------------|-----------------|  
|abstract|Metody, vlastnosti a události|Typ neposkytuje implementaci metody. Typy, které dědí nebo implementují abstraktní metody musí poskytnout implementaci pro metodu. Jedinou výjimkou je, když odvozený typ je sám typu abstraktní. Všechny abstraktní metody jsou virtuální.|  
|privátní, rodiny, sestavení, rodiny a sestavení, rodina nebo sestavení nebo veřejné|Všechny|Definuje usnadnění člena:<br /><br /> private<br /> Přístupné pouze v rámci stejného typu jako člen, nebo v rámci vnořené typy.<br /><br /> Rodina<br /> Je dostupný z v rámci stejného typu jako člen a odvozených typů, které dědí z něj.<br /><br /> sestavení<br /> Přístupné pouze v sestavení, ve kterém je definovaný typ.<br /><br /> Rodina a sestavení<br /> Přístupné pouze typy, které jsou způsobilé pro přístup k řadě a sestavení.<br /><br /> třídu nebo sestavení<br /> Přístupné pouze typy, které jsou způsobilé pro přístup k třídu nebo sestavení.<br /><br /> public<br /> Přístupná z libovolného typu.|  
|finální|Metody, vlastnosti a události|Virtuální metody nelze přepsat v odvozeném typu.|  
|pouze inicializovat|Pole|Hodnota může být pouze inicializována a nelze zapsat po inicializaci.|  
|Instance|Pole, metody, vlastnosti a události|Pokud člen není označen jako `static` (C# a C++), `Shared` (Visual Basic), `virtual` (C# a C++), nebo `Overridable` (Visual Basic), je členem instance (není žádné klíčové slovo instance). Budou existovat libovolný počet kopií takové členy v paměti jsou objekty, které ho používají.|  
|literál|Pole|Hodnota přiřazená k poli je pevná hodnota, známé v době kompilace typu předdefinované hodnoty. Literál pole jsou někdy označovány jako konstanty.|  
|newslot nebo přepsání|Všechny|Definuje, jak člen komunikuje s zděděné členy, které mají stejný podpis:<br /><br /> newslot<br /> Skryje zděděné členy, kteří mají stejným podpisem.<br /><br /> override<br /> Nahradí definici zděděné virtuální metody.<br /><br /> Výchozí hodnota je newslot.|  
|static|Pole, metody, vlastnosti a události|Člen patří typu, který je definován, není pro konkrétní instanci typu; člena existuje, i když není vytvořená instance typu a je sdílena mezi všechny instance typu.|  
|virtual|Metody, vlastnosti a události|Metoda může být implementováno odvozeným typem a vyvolána staticky nebo dynamicky. Pokud je použito dynamické vyvolání, typ instance, která provádí volání v době běhu (spíše než v době kompilace známý typ) určuje, které implementace metoda je volána. Pro vyvolání virtuální metody staticky, možná muset proměnnou přetypovat na typ, který používá požadovanou verzi metody.|  
  
### <a name="overloading"></a>Přetížení  
 Každý typ člen má jedinečný podpis. Metoda podpisy obsahovat název metody a seznam parametrů (pořadí a typy argumentů metody). Několik metod se stejným názvem, může být definován v rámci typu tak dlouho, dokud se liší jejich podpisy. Když jsou definovány dvě nebo více metod se stejným názvem, metoda říká, že je přetížený. Například v <xref:System.Char?displayProperty=nameWithType>, <xref:System.Char.IsDigit%2A> metoda je přetížena. Jedna metoda má <xref:System.Char>. Jiná metoda má <xref:System.String> a <xref:System.Int32>.  
  
> [!NOTE]
>  Návratový typ není považovány za součást signatury metody. To znamená metody nemohou být přetíženy, pokud se liší pouze návratového typu.  
  
### <a name="inheriting-overriding-and-hiding-members"></a>Dědění, přepsání a skrytí členy  
 Odvozený typ dědí všechny členy jeho základní typ; To znamená tito členové jsou definovány tak k dispozici pro odvozený typ. Chování a vlastnosti zděděné členy se dají změnit dvěma způsoby:  
  
-   Odvozený typ skrýt zděděného členu definice nového člena se stejným podpisem. To může být provedeno, aby privátní dříve veřejného člena nebo definovat nové chování pro zděděnou metodu, která je označena jako `final`.  
  
-   Odvozený typ můžete přepsat zděděnou virtuální metodu. Přepsání metody poskytuje novou definici metody, která bude volána na základě typu hodnoty na dobu spuštění, nikoli typ proměnné označuje v době kompilace. Metodu můžete přepsat virtuální metodu pouze v případě, že virtuální metoda není označená jako `final` a nová metoda je dostupný jako virtuální metody.  
  
## <a name="see-also"></a>Viz také  
 [Prohlížeč rozhraní API .NET](/dotnet/api)  
 [Modul Common Language Runtime](../../../docs/standard/clr.md)  
 [Převod typů v rozhraní .NET](../../../docs/standard/base-types/type-conversion.md)
