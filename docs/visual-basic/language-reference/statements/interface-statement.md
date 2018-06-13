---
title: Interface – příkaz (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Interface
helpviewer_keywords:
- interface statement [Visual Basic]
- interfaces [Visual Basic], interface definition
ms.assetid: 8997af73-bda3-4f79-bd41-ca396b610260
ms.openlocfilehash: 31ff9211034438e225494b916045acd07c37810f
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34233909"
---
# <a name="interface-statement-visual-basic"></a>Interface – příkaz (Visual Basic)
Deklaruje název rozhraní a zavádí definice členy, kteří se skládá z rozhraní.  
  
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
|`attributelist`|Volitelné. V tématu [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Volitelné. Může být jedna z následujících akcí:<br /><br /> -   [Veřejné](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [Chráněný](../../../visual-basic/language-reference/modifiers/protected.md)<br />-   [Friend](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [Privátní](../../../visual-basic/language-reference/modifiers/private.md)<br />-  [Chráněné Friend](../../language-reference/modifiers/protected-friend.md)<br/>- [Privátní chráněný](../../language-reference/modifiers/private-protected.md)<br /><br /> V tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Volitelné. V tématu [stínů](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`name`|Požadováno. Název tohoto rozhraní. V tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Volitelné. Určuje, že toto je obecná rozhraní.|  
|`typelist`|Vyžaduje, pokud použijete [z](../../../visual-basic/language-reference/statements/of-clause.md) – klíčové slovo. Seznam parametrů typu pro toto rozhraní. Volitelně můžete každý parametr typu lze deklarovat variant pomocí `In` a `Out` obecné modifikátory. V tématu [zadejte seznam](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Volitelné. Označuje, že toto rozhraní dědí atributy a členy jiné nebo více rozhraní. V tématu [Inherits – příkaz](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`interfacenames`|Vyžaduje, pokud použijete `Inherits` příkaz. Názvy rozhraní, ze kterých je odvozena toto rozhraní.|  
|`modifiers`|Volitelné. Odpovídající parametrů pro člena rozhraní definovaný.|  
|`Property`|Volitelné. Definuje vlastnosti, která je členem rozhraní.|  
|`Function`|Volitelné. Definuje `Function` postup, který je členem rozhraní.|  
|`Sub`|Volitelné. Definuje `Sub` postup, který je členem rozhraní.|  
|`Event`|Volitelné. Definuje událost, která je členem rozhraní.|  
|`Interface`|Volitelné. Definuje rozhraní, které je vnořené v rámci tohoto rozhraní. Definice vnořené rozhraní musí být ukončen s `End Interface` příkaz.|  
|`Class`|Volitelné. Definuje třídu, která je členem rozhraní. Definice třídy člena musí být ukončen s `End Class` příkaz.|  
|`Structure`|Volitelné. Definuje strukturu, která je členem rozhraní. Definice struktury člena musí být ukončen s `End Structure` příkaz.|  
|`membername`|Vyžaduje pro každou vlastnost, postup, události, rozhraní, třída nebo struktura definované jako člen rozhraní. Název člena.|  
|`End Interface`|Ukončí `Interface` definice.|  
  
## <a name="remarks"></a>Poznámky  
 *Rozhraní* definuje sadu členů, například vlastnosti a postupy, které třídy a struktury můžete implementovat. Rozhraní definuje pouze podpis členy a jejich interní chodu.  
  
 Třídu nebo strukturu implementuje rozhraní zadáním kódu pro každého člena definované rozhraní. Nakonec když aplikace vytvoří instanci ze třídy nebo struktura, objekt existuje a spustí v paměti. Další informace najdete v tématu [objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) a [rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 Můžete použít `Interface` pouze na úrovni oboru názvů nebo modul. To znamená *deklarace kontextu* rozhraní musí být zdrojový soubor, obor názvů, třídy, struktury, modul nebo rozhraní a nemůže být procedura nebo bloku. Další informace najdete v tématu [kontexty deklarace a výchozí úrovně přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Výchozí nastavení rozhraní [Friend](../../../visual-basic/language-reference/modifiers/friend.md) přístup. Můžete nastavit jejich úrovně přístupu s modifikátory přístupu. Další informace najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Pravidla  
  
-   **Vnoření rozhraní.** Můžete definovat jedno rozhraní v rámci jiného. Vnější rozhraní nazývá *obsahující rozhraní*, se nazývá vnitřní rozhraní *vnořené rozhraní*.  
  
-   **Deklarace členů.** Když deklarovat vlastnost nebo postupu jako člena rozhraní, který chcete definovat pouze *podpis* této vlastnosti nebo postupu. Jedná se o typ elementu (vlastnost nebo postupu), jeho parametry a typy parametrů a její návratový typ. Z toho důvodu definice člena používá jenom jeden řádek kódu a ukončující příkazy, jako `End Function` nebo `End Property` nejsou platné v rozhraní.  
  
     Naopak když definujete výčet nebo struktura, nebo vnořené třídy nebo rozhraní, je potřeba zahrnout členy jejich data.  
  
-   **Modifikátory člen.** Při definování modulu členy nelze použít žádné modifikátory přístupu ani můžete zadat [sdílené](../../../visual-basic/language-reference/modifiers/shared.md) nebo žádné procedury modifikátor s výjimkou [přetížení](../../../visual-basic/language-reference/modifiers/overloads.md). Je možné deklarovat kteréhokoli člena s [stínů](../../../visual-basic/language-reference/modifiers/shadows.md), a můžete použít [výchozí](../../../visual-basic/language-reference/modifiers/default.md) při definování vlastnosti, a také [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md) nebo [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).  
  
-   **Dědičnost.** Pokud rozhraní používá [dědí příkaz](../../../visual-basic/language-reference/statements/inherits-statement.md), můžete určit jeden nebo více základní rozhraní. Může dědit z dvě rozhraní, i v případě, že každý definují člen se stejným názvem. Pokud tak učiníte, implementující kód musíte použít kvalifikace názvu k určení členů, které implementuje.  
  
     Rozhraní nemůže Zdědit z jiné rozhraní s více omezující úroveň přístupu. Například `Public` rozhraní nemůže Zdědit z `Friend` rozhraní.  
  
     Rozhraní nemůže Zdědit z ní vnořené rozhraní.  
  
-   **Implementace.** Když se používá třídu [implementuje](../../../visual-basic/language-reference/statements/implements-clause.md) příkazů pro toto rozhraní implementovat musí implementovat každý člen definován v rámci rozhraní. Kromě toho každý podpis v kód implementující musí přesně shodovat odpovídající podpis definované v tomto rozhraní. Název člena v implementující kódu však nemá shodovat s názvem člen definovaným v rozhraní.  
  
     Pokud třída je implementace procedury, ho nelze určit postup jako `Shared`.  
  
-   **Výchozí vlastnost.** Rozhraní můžete zadat maximálně jednu vlastnost jako jeho *výchozí vlastnost*, což může být odkazováno bez použití názvu vlastnosti. Zadáte-li tato vlastnost deklarací s [výchozí](../../../visual-basic/language-reference/modifiers/default.md) modifikátor.  
  
     Všimněte si, že to znamená, že rozhraní můžete definovat výchozí vlastnost pouze v případě, že žádný dědí.  
  
## <a name="behavior"></a>Chování  
  
-   **Úroveň přístupu.** Implicitně mít všichni členové rozhraní [veřejné](../../../visual-basic/language-reference/modifiers/public.md) přístup. Při definování člena nelze použít žádné – modifikátor přístupu. Třídu implementující rozhraní však lze deklarovat úroveň přístupu pro každého člena implementovaná.  
  
     Chcete-li přiřadit instanci třídy proměnné, můžete úroveň přístupu svých členů závisí na tom, zda datový typ proměnné základní rozhraní nebo implementující třídu. Toto dokládá následující příklad.  
  
     [!code-vb[VbVbalrStatements#39](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/interface-statement_1.vb)]  
  
     Pokud máte přístup k členy třídy prostřednictvím `varAsInterface`, mají všechna veřejný přístup. Ale pokud jste přístup ke členům prostřednictvím `varAsClass`, `Sub` postup `doSomething` má privátní přístup.  
  
-   **Rozsah.** Rozhraní je v oboru v rámci oboru názvů, třídy, struktury nebo modul.  
  
     Rozsah všech členů rozhraní je celý rozhraní.  
  
-   **Doba platnosti.** Rozhraní sám nemá životnost, ani se její členy. Pokud třída implementuje rozhraní a objekt se vytvoří jako instanci, že třída, objekt má životnost v rámci aplikace, ve kterém je spuštěna. Další informace najdete v tématu "Doba trvání" v [Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Interface` příkaz k definování rozhraní s názvem `thisInterface`, které musí být implementována s `Property` příkaz a `Function` příkaz.  
  
 [!code-vb[VbVbalrStatements#40](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/interface-statement_2.vb)]  
  
 Všimněte si, že `Property` a `Function` příkazy Nezavádět bloky konče `End Property` a `End Function` v rámci rozhraní. Rozhraní definuje pouze signatur její členy. Kompletní `Property` a `Function` bloky se zobrazí v třídu, která implementuje `thisInterface`.  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
 [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Příkaz Module](../../../visual-basic/language-reference/statements/module-statement.md)  
 [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Odchylky obecných rozhraní](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [V](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)  
 [na více systémů](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
