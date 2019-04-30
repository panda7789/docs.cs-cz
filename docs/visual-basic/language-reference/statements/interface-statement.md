---
title: Interface – příkaz (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Interface
helpviewer_keywords:
- interface statement [Visual Basic]
- interfaces [Visual Basic], interface definition
ms.assetid: 8997af73-bda3-4f79-bd41-ca396b610260
ms.openlocfilehash: db39759a804905450e7f8913f45e8ddab39d8416
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61784186"
---
# <a name="interface-statement-visual-basic"></a>Interface – příkaz (Visual Basic)
Deklaruje název rozhraní a zavádí definice členů, které tvoří rozhraní.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
[ <attributelist> ] [ accessmodifier ] [ Shadows ] _  
Interface name [ ( Of typelist ) ]  
    [ Inherits interfacenames ]  
    [ [ modifiers ] Property membername ]  
    [ [ modifiers ] Function membername ]  
    [ [ modifiers ] Sub membername ]  
    [ [ modifiers ] Event membername ]  
    [ [ modifiers ] Interface membername ]  
    [ [ modifiers ] Class membername ]  
    [ [ modifiers ] Structure membername ]  
End Interface  
```  
  
## <a name="parts"></a>Součásti  
  
|Termín|Definice|  
|---|---|  
|`attributelist`|Volitelné. Zobrazit [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Volitelné. Může být jedna z následujících akcí:<br /><br /> -   [Veřejné](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Protected](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend –](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privátní](../../../visual-basic/language-reference/modifiers/private.md)<br />-  [Chráněné typu Friend](../../language-reference/modifiers/protected-friend.md)<br/>- [Privátní, chráněné](../../language-reference/modifiers/private-protected.md)<br /><br /> Zobrazit [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Volitelné. Zobrazit [stíny](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`name`|Povinný parametr. Název tohoto rozhraní. Zobrazit [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Volitelné. Určuje, že se jedná o obecné rozhraní.|  
|`typelist`|Povinné, pokud používáte [z](../../../visual-basic/language-reference/statements/of-clause.md) – klíčové slovo. Seznam parametrů typu pro toto rozhraní. Volitelně můžete každý parametr typu lze deklarovat typ variant pomocí `In` a `Out` obecných parametrů. Zobrazit [seznamu](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Volitelné. Označuje, že toto rozhraní zdědí atributy a jiné rozhraní nebo rozhraní. Zobrazit [Inherits – příkaz](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`interfacenames`|Povinné, pokud používáte `Inherits` příkazu. Názvy rozhraní, ze kterých tato rozhraní je odvozena.|  
|`modifiers`|Volitelné. Odpovídající modifikátory pro tohoto člena rozhraní definuje.|  
|`Property`|Volitelné. Definuje vlastnosti, která je členem rozhraní.|  
|`Function`|Volitelné. Definuje `Function` postup, který je členem rozhraní.|  
|`Sub`|Volitelné. Definuje `Sub` postup, který je členem rozhraní.|  
|`Event`|Volitelné. Definuje událost, která je členem rozhraní.|  
|`Interface`|Volitelné. Definuje rozhraní, které je vnořené v rámci tohoto rozhraní. Definice vnořených rozhraní musí končit `End Interface` příkazu.|  
|`Class`|Volitelné. Definuje třídu, která je členem rozhraní. Definice členů třídy musí končit `End Class` příkazu.|  
|`Structure`|Volitelné. Definuje strukturu, která je členem rozhraní. Definice struktury člena musí končit `End Structure` příkazu.|  
|`membername`|Vyžaduje se pro každou vlastnost, postup, události, rozhraní, třídy nebo struktury definované jako člena rozhraní. Název člena.|  
|`End Interface`|Ukončuje `Interface` definice.|  
  
## <a name="remarks"></a>Poznámky  
 *Rozhraní* definuje sadu členů, například vlastnosti a postupy, které třídy a struktury můžou implementovat. Rozhraní definuje pouze podpisy členů a nejsou jejich vnitřní činnost.  
  
 Třída nebo struktura implementuje rozhraní zadáním kódu pro každého člena definovaného rozhraní. A konečně když aplikace vytvoří instanci z dané třídy nebo struktury, objekt existuje a běží v paměti. Další informace najdete v tématu [objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) a [rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 Můžete použít `Interface` pouze na úrovni oboru názvů nebo modulu. To znamená, *kontextu deklarace* rozhraní musí být zdrojový soubor, obor názvů, třída, struktura, modul nebo rozhraní a nesmí být procedura nebo blok. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Výchozí rozhraní [Friend](../../../visual-basic/language-reference/modifiers/friend.md) přístup. Můžete nastavit jejich úrovně přístupu modifikátory přístupu. Další informace najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>pravidla  
  
- **Vnoření rozhraní.** Můžete definovat jedno rozhraní v rámci jiného. Vnější rozhraní nazývá *obsahující rozhraní*, a volá vnitřní rozhraní *vnořené rozhraní*.  
  
- **Deklarace člena.** Když se vlastnost nebo procedura deklarovat jako člen rozhraní, definujete pouze *podpis* tuto vlastnost nebo procedura. Jedná se o typ elementu (vlastnost nebo procedura), jeho parametry a typy parametrů a její typ vrácené hodnoty. Z tohoto důvodu definice členské používá pouze jeden řádek kódu a ukončující příkazy, jako `End Function` nebo `End Property` nejsou platné v rozhraní.  
  
     Naproti tomu při definování výčtu nebo struktura, nebo vnořené třídy nebo rozhraní, je nutné zahrnout svých datových členů.  
  
- **Člen modifikátory.** Při definování modulu členy nelze použít žádné modifikátory přístupu ani můžete určit [Shared](../../../visual-basic/language-reference/modifiers/shared.md) nebo libovolný postup modifikátor s výjimkou [přetížení](../../../visual-basic/language-reference/modifiers/overloads.md). Můžete deklarovat každého člena, který [stíny](../../../visual-basic/language-reference/modifiers/shadows.md), můžete si [výchozí](../../../visual-basic/language-reference/modifiers/default.md) při definování vlastnosti, stejně jako [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md) nebo [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).  
  
- **Dědičnost.** Pokud používáte rozhraní [dědí příkaz](../../../visual-basic/language-reference/statements/inherits-statement.md), můžete určit jeden nebo více základních rozhraní. Může dědit z dvě rozhraní, i když každá definovat člen se stejným názvem. Pokud tak učiníte, implementující kód používaly kvalifikace názvu určete člen implementuje.  
  
     Rozhraní nemůže dědit z jiného rozhraní s více omezující úroveň přístupu. Například `Public` rozhraní nemůže dědit od třídy `Friend` rozhraní.  
  
     Rozhraní nemůže dědit z rozhraní do něho vnořený.  
  
- **Implementace.** Pokud třída používá [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md) příkaz k implementaci tohoto rozhraní, musí implementovat každého člena definovaného v rámci rozhraní. Každý podpis v prováděcí kód navíc musí přesně odpovídat odpovídající signaturu definovanou v tomto rozhraní. Název člena v implementaci kódu však nemá shodovat s názvem člena, jak jsou definovány v rozhraní.  
  
     Pokud třída implementuje procedury, nelze určit postup jako `Shared`.  
  
- **Výchozí vlastnost.** Rozhraní může určit nejvýše jednu vlastnost jako jeho *výchozí vlastnost*, což může být odkazováno bez použití názvu vlastnosti. Zadejte tyto vlastnosti jeho s deklarací [výchozí](../../../visual-basic/language-reference/modifiers/default.md) modifikátor.  
  
     Všimněte si, že to znamená, že rozhraní můžete definovat výchozí vlastnost jenom v případě, že žádný dědí.  
  
## <a name="behavior"></a>Chování  
  
- **Úroveň přístupu.** Všechny členy rozhraní mají implicitně [veřejné](../../../visual-basic/language-reference/modifiers/public.md) přístup. Když definujete člena, který nelze použít jakékoli modifikátor přístupu. Implementující rozhraní lze však deklarovat úroveň přístupu pro každého člena implementované.  
  
     Pokud přiřadíte instanci třídy do proměnné, úroveň přístupu z jejích členů může záviset na tom, zda datový typ proměnné je základní rozhraní nebo implementující třídu. Toto dokládá následující příklad.  
  
     [!code-vb[VbVbalrStatements#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#39)]  
  
     Pokud jste přístup ke členům třídy pomocí `varAsInterface`, všichni mají veřejný přístup. Ale pokud získáte přístup k členům pomocí `varAsClass`, `Sub` postup `doSomething` má privátní přístup.  
  
- **Obor.** Rozhraní je v oboru v celém oboru názvů, třídy, struktury nebo modulu.  
  
     Obor každého člena rozhraní je celé rozhraní.  
  
- **Doba platnosti.** Rozhraní sama nemá životnost, ani dělat jeho členů. Pokud třída implementuje rozhraní a objekt vytvořen jako instance, že třídu, má objekt životního cyklu aplikace, ve kterém je spuštěná. Další informace najdete v tématu "Životnost" [Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Interface` příkaz k definování rozhraní s názvem `thisInterface`, které musí být implementované pomocí `Property` příkazu a `Function` příkaz.  
  
 [!code-vb[VbVbalrStatements#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#40)]  
  
 Všimněte si, že `Property` a `Function` příkazy nezavádí bloky končí `End Property` a `End Function` v rámci rozhraní. Rozhraní definuje pouze podpisy členů. Kompletní `Property` a `Function` bloky se zobrazí ve třídě, která implementuje `thisInterface`.  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)
- [Příkaz Module](../../../visual-basic/language-reference/statements/module-statement.md)
- [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Odchylky obecných rozhraní](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [V](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [navýšení kapacity](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
