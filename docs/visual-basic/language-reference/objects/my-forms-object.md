---
title: My.Forms – objekt
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 001f6fbfae2467ea0af5e98ca041b694d1e7b8f9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372437"
---
# <a name="myforms-object"></a>My.Forms – objekt

Poskytuje vlastnosti pro přístup k instanci každého formuláře Windows deklarovaného v aktuálním projektu.

## <a name="remarks"></a>Poznámky

`My.Forms`Objekt poskytuje instanci každého formuláře v aktuálním projektu. Název vlastnosti je stejný jako název formuláře, ke kterému vlastnost přistupuje.

K formulářům poskytnutým `My.Forms` objektem můžete přistupovat pomocí názvu formuláře bez kvalifikace. Vzhledem k tomu, že název vlastnosti je stejný jako název typu formuláře, umožňuje přístup k formuláři, jako by měl výchozí instanci. Například `My.Forms.Form1.Show` je ekvivalentem k `Form1.Show` .

`My.Forms`Objekt zpřístupňuje pouze formuláře přidružené k aktuálnímu projektu. Neposkytuje přístup k formulářům deklarovaným v odkazovaných knihovnách DLL. Chcete-li získat přístup k formuláři, který poskytuje knihovna DLL, je nutné použít kvalifikovaný název formuláře, který je napsán jako *Název_souboru_DLL*. *Formace*.

Vlastnost můžete použít <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> k získání kolekce všech otevřených formulářů aplikace.

Objekt a jeho vlastnosti jsou k dispozici pouze pro aplikace systému Windows.

## <a name="properties"></a>Vlastnosti

Každá vlastnost `My.Forms` objektu poskytuje přístup k instanci formuláře v aktuálním projektu. Název vlastnosti je stejný jako název formuláře, ke kterému vlastnost přistupuje, a typ vlastnosti je stejný jako typ formuláře.

> [!NOTE]
> Pokud dojde ke kolizi názvů, název vlastnosti pro přístup k formuláři je *RootNamespace*_*Namespace* \_ *FormName*. Zvažte například dva formuláře s názvem, `Form1.` Pokud je jeden z těchto formulářů v kořenovém oboru názvů `WindowsApplication1` a v oboru názvů `Namespace1` , k tomuto formuláři byste měli přistupovat prostřednictvím `My.Forms.WindowsApplication1_Namespace1_Form1` .

`My.Forms`Objekt poskytuje přístup k instanci hlavního formuláře aplikace, který byl vytvořen při spuštění. Pro všechny ostatní formuláře `My.Forms` vytvoří objekt novou instanci formuláře při jeho otevření a uložení. Následné pokusy o přístup k této vlastnosti vrátí tuto instanci formuláře.

Formulář můžete uvolnit tak, že mu přiřadíte `Nothing` vlastnost pro tento formulář. Vlastnost setter volá <xref:System.Windows.Forms.Form.Close%2A> metodu formuláře a potom přiřadí `Nothing` uloženou hodnotu. Pokud přiřadíte jinou hodnotu než `Nothing` k vlastnosti, metoda setter vyvolá <xref:System.ArgumentException> výjimku.

Můžete otestovat, zda vlastnost `My.Forms` objektu ukládá instanci formuláře pomocí `Is` `IsNot` operátoru OR. Tyto operátory můžete použít ke kontrole, zda je hodnota vlastnosti `Nothing` .

> [!NOTE]
> `Is`Operátor OR obvykle `IsNot` musí číst hodnotu vlastnosti pro provedení porovnání. Pokud je však vlastnost aktuálně uložena `Nothing` , vlastnost vytvoří novou instanci formuláře a následně vrátí tuto instanci. Nicméně kompilátor Visual Basic zpracovává vlastnosti `My.Forms` objektu odlišně a umožňuje `Is` `IsNot` operátoru OR kontrolovat stav vlastnosti bez změny její hodnoty.

## <a name="example"></a>Příklad

Tento příklad změní název výchozího `SidebarMenu` formuláře.

[!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]

Aby tento příklad fungoval, projekt musí mít formulář s názvem `SidebarMenu` .

Tento kód bude fungovat pouze v projektu aplikace systému Windows.

## <a name="requirements"></a>Požadavky

### <a name="availability-by-project-type"></a>Dostupnost podle typu projektu

|Typ projektu|K dispozici|
|---|---|
|Aplikace systému Windows|**Ano**|
|Knihovna tříd|Ne|
|Konzolová aplikace|Ne|
|Knihovna ovládacích prvků Windows|Ne|
|Knihovna webového ovládacího prvku|Ne|
|Služba systému Windows|Ne|
|Web|Ne|

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [Objekty](index.md)
- [Is – operátor](../operators/is-operator.md)
- [IsNot – operátor](../operators/isnot-operator.md)
- [Přístup k formulářům aplikace](../../developing-apps/programming/accessing-application-forms.md)
