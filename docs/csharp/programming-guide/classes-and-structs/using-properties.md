---
title: Použití vlastností – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- set accessor [C#]
- get accessor [C#]
- properties [C#], about properties
ms.assetid: f7f67b05-0983-4cdb-96af-1855d24c967c
ms.openlocfilehash: fdaa4b511b18495d2a35f72ee017a01aab0b4ee8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922055"
---
# <a name="using-properties-c-programming-guide"></a>Použití vlastností (Průvodce programováním v C#)
Vlastnosti kombinují aspekty obou polí a metod. Pro uživatele objektu se zobrazí vlastnost, která má být pole a přístup k vlastnosti vyžaduje stejnou syntaxi. Pro Implementátor třídy je vlastnost jedním nebo dvěma bloky kódu, které představují přistupující objekt [Get](../../language-reference/keywords/get.md) nebo přístupový objekt [set](../../language-reference/keywords/set.md) . Blok kódu pro `get` přistupující objekt je proveden při čtení vlastnosti. blok kódu `set` pro přistupující objekt je spuštěn, když je vlastnost přiřazena nová hodnota. Vlastnost bez `set` přístupového objektu je považována za jen pro čtení. Vlastnost bez `get` přístupového objektu je považována za jen pro zápis. Vlastnost, která má oba přístupové objekty, je pro čtení i zápis.  
  
 Na rozdíl od polí nejsou vlastnosti klasifikovány jako proměnné. Proto nelze vlastnost předat jako parametr [ref](../../language-reference/keywords/ref.md) nebo [out](../../language-reference/keywords/out-parameter-modifier.md) .  
  
 Vlastnosti mají mnoho použití: může ověřit data před tím, než povolí změnu. mohou transparentně vystavovat data pro třídu, kde jsou data skutečně načtena z nějakého jiného zdroje, jako je například databáze. mohou provést akci při změně dat, jako je například vyvolání události nebo změna hodnoty jiných polí.  
  
 Vlastnosti jsou deklarovány v bloku třídy zadáním úrovně přístupu pole, za nímž následuje typ vlastnosti následovaný názvem vlastnosti a následným blokem kódu, který deklaruje `get`přistupující objekt nebo `set` přistupující objekt. Příklad:  
  
 [!code-csharp[csProgGuideProperties#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#7)]  
  
 V tomto příkladu `Month` je deklarován jako vlastnost, aby `set` přístupový objekt `Month` mohl zajistit, aby byla hodnota nastavena v rozmezí od 1 do 12. `Month` Vlastnost používá soukromé pole ke sledování skutečné hodnoty. Skutečné umístění dat vlastnosti se často označuje jako "záložní úložiště" vlastnosti. Vlastnosti pro použití privátních polí jako záložního úložiště je běžné. Pole je označeno jako soukromé, aby se zajistilo, že lze změnit pouze voláním vlastnosti. Další informace o omezeních veřejného a soukromého přístupu najdete v tématu [modifikátory přístupu](./access-modifiers.md).  
  
 Automaticky implementované vlastnosti poskytují zjednodušenou syntaxi pro jednoduché deklarace vlastností. Další informace najdete v tématu věnovaném [automaticky implementovaným vlastnostem](./auto-implemented-properties.md).  
  
## <a name="the-get-accessor"></a>Přístupový objekt get  
 Tělo `get` přístupového objektu se podobá metodě. Musí vracet hodnotu typu vlastnosti. Provedení `get` přístupového objektu je ekvivalentní k načtení hodnoty pole. Například pokud vracíte soukromou proměnnou z `get` přístupového objektu a optimalizace jsou povoleny, volání `get` metody přistupujícího objektu je vloženo kompilátorem, takže neexistuje žádná režie volání metody. Metoda virtuálního `get` přístupového objektu však nemůže být vložena, protože kompilátor neví v době kompilace, kterou lze skutečně volat v době běhu. Následuje `get` přístup, který vrací hodnotu soukromého pole `name`:  
  
 [!code-csharp[csProgGuideProperties#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#8)]  
  
 Když odkazujete na vlastnost, s výjimkou cíle přiřazení, `get` je vyvolán přistupující objekt pro čtení hodnoty vlastnosti. Příklad:  
  
 [!code-csharp[csProgGuideProperties#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#9)]  
  
 Přistupující objekt musí končit příkazem [return](../../language-reference/keywords/return.md) nebo throw a ovládací prvek nemůže přesměrovat tělo přistupujícího objektu. [](../../language-reference/keywords/throw.md) `get`  
  
 Je to špatný styl programování ke změně stavu objektu pomocí `get` přístupového objektu. Například následující přistupující objekt vytváří vedlejší účinek změny stavu objektu při každém přístupu k `number` poli.  
  
 [!code-csharp[csProgGuideProperties#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#10)]  
  
 `get` Přístupový objekt lze použít k vrácení hodnoty pole nebo k jejímu výpočtu a vrácení. Příklad:  
  
 [!code-csharp[csProgGuideProperties#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#11)]  
  
 Pokud v předchozím segmentu kódu nepřiřazujete hodnotu `Name` vlastnosti, vrátí hodnotu NEDEF.  
  
## <a name="the-set-accessor"></a>Přístupový objekt set  
 Přistupující objekt se podobá metodě, jejíž návratový typ je [void.](../../language-reference/keywords/void.md) `set` Používá implicitní parametr s názvem `value`, jehož typ je typ vlastnosti. V následujícím příkladu `set` je přistupující objekt přidán `Name` do vlastnosti:  
  
 [!code-csharp[csProgGuideProperties#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#12)]  
  
 Když přiřadíte hodnotu vlastnosti, `set` přistupující objekt je vyvolán pomocí argumentu, který poskytuje novou hodnotu. Příklad:  
  
 [!code-csharp[csProgGuideProperties#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#13)]  
  
 Použití implicitního názvu `value`parametru, pro deklaraci lokální proměnné `set` v přístupovém objektu, je chybné.  
  
## <a name="remarks"></a>Poznámky  
 Vlastnosti mohou být označeny jako `public`, `private`, `protected`, `internal` `protected internal` nebo .`private protected` Tyto modifikátory přístupu definují, jak budou uživatelé třídy mít přístup k vlastnosti. Přístupové objekty `set` a pro stejnou vlastnost mohou mít různé modifikátory přístupu. `get` Například `get` může být `public` povolení přístupu jen pro čtení zvenčí mimo typ a `set` může být `private` nebo `protected`. Další informace najdete v tématu [modifikátory přístupu](./access-modifiers.md).  
  
 Vlastnost může být deklarována jako statická vlastnost pomocí `static` klíčového slova. Tato vlastnost zpřístupňuje volajícím kdykoli, a to i v případě, že žádná instance třídy neexistuje. Další informace naleznete v tématu [statické třídy a statické členy třídy](./static-classes-and-static-class-members.md).  
  
 Vlastnost může být označena jako virtuální vlastnost pomocí klíčového slova [Virtual](../../language-reference/keywords/virtual.md) . To umožňuje odvozeným třídám přepsat chování vlastnosti pomocí klíčového slova [override](../../language-reference/keywords/override.md) . Další informace o těchto možnostech naleznete v tématu [Dědičnost](./inheritance.md).  
  
 Vlastnost přepisujecí virtuální vlastnost může být také [zapečetěná](../../language-reference/keywords/sealed.md)a specifikuje, že pro odvozené třídy už není virtuální. Nakonec může být vlastnost deklarována jako [abstraktní](../../language-reference/keywords/abstract.md). To znamená, že ve třídě není žádná implementace, a odvozené třídy musí napsat svou vlastní implementaci. Další informace o těchto možnostech naleznete v tématu [abstraktní a zapečetěné třídy a členy třídy](./abstract-and-sealed-classes-and-class-members.md).  
  
> [!NOTE]
> Použití modifikátoru [Virtual](../../language-reference/keywords/virtual.md), [abstract](../../language-reference/keywords/abstract.md)nebo [override](../../language-reference/keywords/override.md) u přístupového objektu [statické](../../language-reference/keywords/static.md) vlastnosti je chybné.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje vlastnosti instance, static a jen pro čtení. Přijímá jméno zaměstnance z klávesnice, zvyšuje hodnotu `NumberOfEmployees` o 1 a zobrazuje jméno a číslo zaměstnance.  
  
 [!code-csharp[csProgGuideProperties#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#2)]  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak získat přístup k vlastnosti v základní třídě, která je skryta jinou vlastností, která má stejný název v odvozené třídě.  
  
 [!code-csharp[csProgGuideProperties#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#3)]  
  
 Níže jsou uvedené důležité body v předchozím příkladu:  
  
- Vlastnost `Name` v odvozené třídě skrývá vlastnost `Name` v základní třídě. V takovém případě `new` se modifikátor používá v deklaraci vlastnosti v odvozené třídě:  
  
     [!code-csharp[csProgGuideProperties#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#4)]  
  
- Přetypování `(Employee)` se používá pro přístup k skryté vlastnosti v základní třídě:  
  
     [!code-csharp[csProgGuideProperties#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#5)]  
  
     Další informace o skrývání členů naleznete v tématu [nový modifikátor](../../language-reference/keywords/new-modifier.md).  
  
## <a name="example"></a>Příklad  
 V tomto `Cube` příkladu dvě třídy, `Square` `Shape`implementujte abstraktní třídu, a přepište její abstraktní `Area` vlastnost. Všimněte si použití modifikátoru [přepsání](../../language-reference/keywords/override.md) u vlastností. Program přijme stranu jako vstup a vypočítá oblasti pro čtvercovou a datovou krychli. Také přijme oblast jako vstup a vypočte odpovídající stranu pro čtvercovou a datovou krychli.  
  
 [!code-csharp[csProgGuideProperties#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#6)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Vlastnosti](./properties.md)
- [Vlastnosti rozhraní](./interface-properties.md)
- [Automaticky implementované vlastnosti](./auto-implemented-properties.md)
