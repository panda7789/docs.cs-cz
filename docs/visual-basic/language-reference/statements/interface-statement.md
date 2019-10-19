---
title: Interface – příkaz (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Interface
helpviewer_keywords:
- interface statement [Visual Basic]
- interfaces [Visual Basic], interface definition
ms.assetid: 8997af73-bda3-4f79-bd41-ca396b610260
ms.openlocfilehash: 68590702835e47e5f0f2e0380bc0fe4017d5eb15
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582673"
---
# <a name="interface-statement-visual-basic"></a>Interface – příkaz (Visual Basic)
Deklaruje název rozhraní a zavádí definice členů, které rozhraní zahrnuje.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
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
|`attributelist`|Volitelné. Viz [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md).|  
|`accessmodifier`|Volitelné. Může to být jedna z následujících:<br /><br /> -   [veřejné](../../../visual-basic/language-reference/modifiers/public.md)<br />-   [chráněno](../../../visual-basic/language-reference/modifiers/protected.md)<br />-    –[přítel](../../../visual-basic/language-reference/modifiers/friend.md)<br />-   [privátní](../../../visual-basic/language-reference/modifiers/private.md)<br />[přítel chráněný](../../language-reference/modifiers/protected-friend.md) -  <br/>- [Private Protected](../../language-reference/modifiers/private-protected.md)<br /><br /> Podívejte [se na úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Volitelné. Viz [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).|  
|`name`|Požadováno. Název tohoto rozhraní Viz [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Volitelné. Určuje, že se jedná o obecné rozhraní.|  
|`typelist`|Povinné, pokud použijete klíčové slovo [of](../../../visual-basic/language-reference/statements/of-clause.md) . Seznam parametrů typu pro toto rozhraní Volitelně lze každý parametr typu deklarovat jako typ variant pomocí `In` a `Out` obecných modifikátorů. Viz [seznam typů](../../../visual-basic/language-reference/statements/type-list.md).|  
|`Inherits`|Volitelné. Označuje, že toto rozhraní dědí atributy a členy jiného rozhraní nebo rozhraní. Viz [příkaz Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md).|  
|`interfacenames`|Vyžaduje se, pokud použijete příkaz `Inherits`. Názvy rozhraní, ze kterých je toto rozhraní odvozeno.|  
|`modifiers`|Volitelné. Odpovídající modifikátory pro člena rozhraní, který je definován.|  
|`Property`|Volitelné. Definuje vlastnost, která je členem rozhraní.|  
|`Function`|Volitelné. Definuje proceduru `Function`, která je členem rozhraní.|  
|`Sub`|Volitelné. Definuje proceduru `Sub`, která je členem rozhraní.|  
|`Event`|Volitelné. Definuje událost, která je členem rozhraní.|  
|`Interface`|Volitelné. Definuje rozhraní, které je vnořené v rámci tohoto rozhraní. Definice vnořeného rozhraní musí končit příkazem `End Interface`.|  
|`Class`|Volitelné. Definuje třídu, která je členem rozhraní. Definice členské třídy musí končit příkazem `End Class`.|  
|`Structure`|Volitelné. Definuje strukturu, která je členem rozhraní. Definice struktury členů musí být ukončena příkazem `End Structure`.|  
|`membername`|Požadováno pro každou vlastnost, proceduru, událost, rozhraní, třídu nebo strukturu definovanou jako člen rozhraní. Název člena.|  
|`End Interface`|Ukončí definici `Interface`.|  
  
## <a name="remarks"></a>Poznámky  
 *Rozhraní* definuje sadu členů, jako jsou například vlastnosti a postupy, které mohou implementovat třídy a struktury. Rozhraní definuje pouze podpisy členů a nikoli jejich interní úkoly.  
  
 Třída nebo struktura implementuje rozhraní zadáním kódu pro každého člena definovaného rozhraním. Nakonec, když aplikace vytvoří instanci z této třídy nebo struktury, objekt existuje a spustí se v paměti. Další informace naleznete v tématu [objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md) a [rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md).  
  
 @No__t_0 můžete použít jenom na úrovni oboru názvů nebo modulu. To znamená, že *kontext deklarace* pro rozhraní musí být zdrojový soubor, obor názvů, třída, struktura, modul nebo rozhraní a nemůže být procedura nebo blok. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).  
  
 Ve výchozím nastavení rozhraní [přítel](../../../visual-basic/language-reference/modifiers/friend.md) přístup. Můžete upravit jejich úrovně přístupu modifikátory přístupu. Další informace najdete v tématu [úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Pravidly  
  
- **Vnořování rozhraní.** Můžete definovat jedno rozhraní v rámci jiného. Vnější rozhraní se nazývá *obsahující rozhraní*a vnitřní rozhraní se nazývá *vnořené rozhraní*.  
  
- **Deklarace člena** Při deklaraci vlastnosti nebo procedury jako člena rozhraní definujete pouze *podpis* této vlastnosti nebo procedury. To zahrnuje typ elementu (vlastnost nebo procedura), jeho parametry a typy parametrů a jeho návratový typ. Z tohoto důvodu definice členů používá pouze jeden řádek kódu a ukončovací příkazy, jako `End Function` nebo `End Property`, nejsou v rozhraní platné.  
  
     Naproti tomu, při definování výčtu nebo struktury, nebo vnořené třídy nebo rozhraní, je nutné zahrnout jejich datové členy.  
  
- **Modifikátory členů.** Při definování členů modulu nelze použít žádné modifikátory přístupu, ani nelze zadat [Shared](../../../visual-basic/language-reference/modifiers/shared.md) ani modifikátory procedury s výjimkou [přetížení](../../../visual-basic/language-reference/modifiers/overloads.md). Můžete deklarovat libovolného člena pomocí [stínů](../../../visual-basic/language-reference/modifiers/shadows.md)a můžete použít [výchozí](../../../visual-basic/language-reference/modifiers/default.md) při definování vlastnosti a také [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md) nebo [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md).  
  
- **Dědičnost.** Pokud rozhraní používá [příkaz Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md), můžete zadat jedno nebo více základních rozhraní. Můžete Zdědit ze dvou rozhraní i v případě, že každý definuje člena se stejným názvem. Pokud to uděláte, implementace kódu musí použít kvalifikaci názvu k určení, který člen implementuje.  
  
     Rozhraní nemůže dědit z jiného rozhraní s více omezující úrovní přístupu. Rozhraní `Public` například nemůže dědit z rozhraní `Friend`.  
  
     Rozhraní nemůže dědit z rozhraní, které je v něm vnořené.  
  
- **Provádění.** Pokud třída používá příkaz [Implements](../../../visual-basic/language-reference/statements/implements-clause.md) pro implementaci tohoto rozhraní, musí implementovat každého člena definovaného v rámci rozhraní. Kromě toho každý podpis v implementaci kódu musí přesně odpovídat odpovídajícímu podpisu definovanému v tomto rozhraní. Název členu v implementaci kódu však nemusí odpovídat názvu člena, jak je definován v rozhraní.  
  
     Když třída implementuje proceduru, nemůže určit proceduru jako `Shared`.  
  
- **Výchozí vlastnost.** Rozhraní může zadat maximálně jednu vlastnost jako *výchozí vlastnost*, na kterou se dá odkazovat bez použití názvu vlastnosti. Tuto vlastnost určíte tak, že ji deklarujete s [výchozím](../../../visual-basic/language-reference/modifiers/default.md) modifikátorem.  
  
     Všimněte si, že rozhraní může definovat výchozí vlastnost pouze v případě, že je děděna není.  
  
## <a name="behavior"></a>Předvídatelně  
  
- **Úroveň přístupu.** Všechny členy rozhraní mají implicitně [veřejný](../../../visual-basic/language-reference/modifiers/public.md) přístup. Při definování člena nelze použít žádný modifikátor přístupu. Třída implementující rozhraní však může deklarovat úroveň přístupu pro každého implementovaného člena.  
  
     Pokud přiřadíte instanci třídy proměnné, úroveň přístupu jeho členů může záviset na tom, zda je datovým typem proměnné základní rozhraní nebo implementující třída. Toto dokládá následující příklad.  
  
     [!code-vb[VbVbalrStatements#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#39)]  
  
     Pokud přistupujete ke členům třídy prostřednictvím `varAsInterface`, všichni mají veřejný přístup. Pokud však ke členům přistupujete prostřednictvím `varAsClass`, má `Sub` procedura `doSomething` privátní přístup.  
  
- **Oboru.** Rozhraní je v rozsahu celého oboru názvů, třídy, struktury nebo modulu.  
  
     Rozsah každého člena rozhraní je celé rozhraní.  
  
- **Platné.** Rozhraní samo o sobě nemá dobu života ani jeho členy. Když třída implementuje rozhraní a objekt je vytvořen jako instance této třídy, má objekt životnost v rámci aplikace, ve které je spuštěna. Další informace naleznete v části "doba života" v [příkazu třídy](../../../visual-basic/language-reference/statements/class-statement.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá příkaz `Interface` k definování rozhraní s názvem `thisInterface`, které musí být implementovány pomocí příkazu `Property` a příkazu `Function`.  
  
 [!code-vb[VbVbalrStatements#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#40)]  
  
 Všimněte si, že příkazy `Property` a `Function` nezavádějí bloky končící `End Property` a `End Function` v rámci rozhraní. Rozhraní definuje pouze signatury svých členů. Všechny bloky `Property` a `Function` se zobrazí ve třídě, která implementuje `thisInterface`.  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)
- [Příkaz Module](../../../visual-basic/language-reference/statements/module-statement.md)
- [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Obecné typy v Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Odchylky obecných rozhraní](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [Pro](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
- [Mimo](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
