---
title: Interface – příkaz
ms.date: 05/12/2018
f1_keywords:
- vb.Interface
helpviewer_keywords:
- interface statement [Visual Basic]
- interfaces [Visual Basic], interface definition
ms.assetid: 8997af73-bda3-4f79-bd41-ca396b610260
ms.openlocfilehash: 02d258084aaaa53dcc559cfaa0dec27556351037
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404483"
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
  
|Pojem|Definice|  
|---|---|  
|`attributelist`|Nepovinný parametr. Viz [seznam atributů](attribute-list.md).|  
|`accessmodifier`|Nepovinný parametr. Může to být jedna z následujících:<br /><br /> -   [Republik](../modifiers/public.md)<br />-   [Proti](../modifiers/protected.md)<br />-   [Friend](../modifiers/friend.md)<br />-   [Hlášen](../modifiers/private.md)<br />-  [Chráněný přítel](../modifiers/protected-friend.md)<br/>- [Soukromé chráněné](../modifiers/private-protected.md)<br /><br /> Podívejte [se na úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).|  
|`Shadows`|Nepovinný parametr. Viz [Shadows](../modifiers/shadows.md).|  
|`name`|Povinná hodnota. Název tohoto rozhraní Viz [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md).|  
|`Of`|Nepovinný parametr. Určuje, že se jedná o obecné rozhraní.|  
|`typelist`|Povinné, pokud použijete klíčové slovo [of](of-clause.md) . Seznam parametrů typu pro toto rozhraní Volitelně lze každý parametr typu deklarovat jako variant pomocí `In` a `Out` obecných modifikátorů. Viz [seznam typů](type-list.md).|  
|`Inherits`|Nepovinný parametr. Označuje, že toto rozhraní dědí atributy a členy jiného rozhraní nebo rozhraní. Viz [příkaz Inherits](inherits-statement.md).|  
|`interfacenames`|Vyžaduje se, pokud použijete `Inherits` příkaz. Názvy rozhraní, ze kterých je toto rozhraní odvozeno.|  
|`modifiers`|Nepovinný parametr. Odpovídající modifikátory pro člena rozhraní, který je definován.|  
|`Property`|Nepovinný parametr. Definuje vlastnost, která je členem rozhraní.|  
|`Function`|Nepovinný parametr. Definuje `Function` proceduru, která je členem rozhraní.|  
|`Sub`|Nepovinný parametr. Definuje `Sub` proceduru, která je členem rozhraní.|  
|`Event`|Nepovinný parametr. Definuje událost, která je členem rozhraní.|  
|`Interface`|Nepovinný parametr. Definuje rozhraní, které je vnořené v rámci tohoto rozhraní. Definice vnořeného rozhraní musí končit `End Interface` příkazem.|  
|`Class`|Nepovinný parametr. Definuje třídu, která je členem rozhraní. Definice členské třídy musí končit `End Class` příkazem.|  
|`Structure`|Nepovinný parametr. Definuje strukturu, která je členem rozhraní. Definice struktury členů musí končit `End Structure` příkazem.|  
|`membername`|Požadováno pro každou vlastnost, proceduru, událost, rozhraní, třídu nebo strukturu definovanou jako člen rozhraní. Název členu|  
|`End Interface`|Ukončí `Interface` definici.|  
  
## <a name="remarks"></a>Poznámky  
 *Rozhraní* definuje sadu členů, jako jsou například vlastnosti a postupy, které mohou implementovat třídy a struktury. Rozhraní definuje pouze podpisy členů a nikoli jejich interní úkoly.  
  
 Třída nebo struktura implementuje rozhraní zadáním kódu pro každého člena definovaného rozhraním. Nakonec, když aplikace vytvoří instanci z této třídy nebo struktury, objekt existuje a spustí se v paměti. Další informace naleznete v tématu [objekty a třídy](../../programming-guide/language-features/objects-and-classes/index.md) a [rozhraní](../../programming-guide/language-features/interfaces/index.md).  
  
 Můžete použít `Interface` pouze v oboru názvů nebo na úrovni modulu. To znamená, že *kontext deklarace* pro rozhraní musí být zdrojový soubor, obor názvů, třída, struktura, modul nebo rozhraní a nemůže být procedura nebo blok. Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](declaration-contexts-and-default-access-levels.md).  
  
 Ve výchozím nastavení rozhraní [přítel](../modifiers/friend.md) přístup. Můžete upravit jejich úrovně přístupu modifikátory přístupu. Další informace najdete v tématu [úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).  
  
## <a name="rules"></a>Pravidla  
  
- **Vnořování rozhraní.** Můžete definovat jedno rozhraní v rámci jiného. Vnější rozhraní se nazývá *obsahující rozhraní*a vnitřní rozhraní se nazývá *vnořené rozhraní*.  
  
- **Deklarace člena** Při deklaraci vlastnosti nebo procedury jako člena rozhraní definujete pouze *podpis* této vlastnosti nebo procedury. To zahrnuje typ elementu (vlastnost nebo procedura), jeho parametry a typy parametrů a jeho návratový typ. Z tohoto důvodu definice členů používá pouze jeden řádek kódu a ukončovací příkazy, jako je nebo, nejsou `End Function` `End Property` v rozhraní platné.  
  
     Naproti tomu, při definování výčtu nebo struktury, nebo vnořené třídy nebo rozhraní, je nutné zahrnout jejich datové členy.  
  
- **Modifikátory členů.** Při definování členů modulu nelze použít žádné modifikátory přístupu, ani nelze zadat [Shared](../modifiers/shared.md) ani modifikátory procedury s výjimkou [přetížení](../modifiers/overloads.md). Můžete deklarovat libovolného člena pomocí [stínů](../modifiers/shadows.md)a můžete použít [výchozí](../modifiers/default.md) při definování vlastnosti a také [jen pro čtení](../modifiers/readonly.md) nebo [WriteOnly](../modifiers/writeonly.md).  
  
- **Dědičnost.** Pokud rozhraní používá [příkaz Inherits](inherits-statement.md), můžete zadat jedno nebo více základních rozhraní. Můžete Zdědit ze dvou rozhraní i v případě, že každý definuje člena se stejným názvem. Pokud to uděláte, implementace kódu musí použít kvalifikaci názvu k určení, který člen implementuje.  
  
     Rozhraní nemůže dědit z jiného rozhraní s více omezující úrovní přístupu. `Public`Rozhraní nemůže například dědit z `Friend` rozhraní.  
  
     Rozhraní nemůže dědit z rozhraní, které je v něm vnořené.  
  
- **Provádění.** Pokud třída používá příkaz [Implements](implements-clause.md) pro implementaci tohoto rozhraní, musí implementovat každého člena definovaného v rámci rozhraní. Kromě toho každý podpis v implementaci kódu musí přesně odpovídat odpovídajícímu podpisu definovanému v tomto rozhraní. Název členu v implementaci kódu však nemusí odpovídat názvu člena, jak je definován v rozhraní.  
  
     Když třída implementuje proceduru, nemůže určit proceduru jako `Shared` .  
  
- **Výchozí vlastnost.** Rozhraní může zadat maximálně jednu vlastnost jako *výchozí vlastnost*, na kterou se dá odkazovat bez použití názvu vlastnosti. Tuto vlastnost určíte tak, že ji deklarujete s [výchozím](../modifiers/default.md) modifikátorem.  
  
     Všimněte si, že rozhraní může definovat výchozí vlastnost pouze v případě, že je děděna není.  
  
## <a name="behavior"></a>Chování  
  
- **Úroveň přístupu.** Všechny členy rozhraní mají implicitně [veřejný](../modifiers/public.md) přístup. Při definování člena nelze použít žádný modifikátor přístupu. Třída implementující rozhraní však může deklarovat úroveň přístupu pro každého implementovaného člena.  
  
     Pokud přiřadíte instanci třídy proměnné, úroveň přístupu jeho členů může záviset na tom, zda je datovým typem proměnné základní rozhraní nebo implementující třída. Toto dokládá následující příklad.  
  
     [!code-vb[VbVbalrStatements#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#39)]  
  
     Pokud přistupujete ke členům třídy prostřednictvím `varAsInterface` , všichni mají veřejný přístup. Pokud však ke členům přistupujete prostřednictvím `varAsClass` , `Sub` má tento postup `doSomething` privátní přístup.  
  
- **Oboru.** Rozhraní je v rozsahu celého oboru názvů, třídy, struktury nebo modulu.  
  
     Rozsah každého člena rozhraní je celé rozhraní.  
  
- **Platné.** Rozhraní samo o sobě nemá dobu života ani jeho členy. Když třída implementuje rozhraní a objekt je vytvořen jako instance této třídy, má objekt životnost v rámci aplikace, ve které je spuštěna. Další informace naleznete v části "doba života" v [příkazu třídy](class-statement.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Interface` příkaz k definování rozhraní s názvem `thisInterface` , které musí být implementováno pomocí `Property` příkazu a `Function` příkazu.  
  
 [!code-vb[VbVbalrStatements#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#40)]  
  
 Všimněte si, `Property` že `Function` příkazy a nezavádí bloky končící `End Property` na a `End Function` v rámci rozhraní. Rozhraní definuje pouze signatury svých členů. Úplný `Property` blok a `Function` se zobrazí ve třídě, která implementuje `thisInterface` .  
  
## <a name="see-also"></a>Viz také

- [Rozhraní](../../programming-guide/language-features/interfaces/index.md)
- [Class – příkaz](class-statement.md)
- [Module – příkaz](module-statement.md)
- [Structure – příkaz](structure-statement.md)
- [Property – příkaz](property-statement.md)
- [Function – příkaz](function-statement.md)
- [Sub – příkaz](sub-statement.md)
- [Obecné typy v Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Odchylky obecných rozhraní](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [V](../modifiers/in-generic-modifier.md)
- [Mimo](../modifiers/out-generic-modifier.md)
