---
title: My.Forms – objekt
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: db86704fdc8120ccac5f4489c80a515834ad888f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350363"
---
# <a name="myforms-object"></a>My.Forms – objekt

Poskytuje vlastnosti pro přístup k instanci každého formuláře Windows deklarovaného v aktuálním projektu.

## <a name="remarks"></a>Poznámky

Objekt `My.Forms` poskytuje instanci každého formuláře v aktuálním projektu. Název vlastnosti je stejný jako název formuláře, ke kterému vlastnost přistupuje.

K formulářům poskytovaným objektem `My.Forms` můžete přistupovat pomocí názvu formuláře bez kvalifikace. Vzhledem k tomu, že název vlastnosti je stejný jako název typu formuláře, umožňuje přístup k formuláři, jako by měl výchozí instanci. Například `My.Forms.Form1.Show` je ekvivalentem `Form1.Show`.

Objekt `My.Forms` zpřístupňuje pouze formuláře přidružené k aktuálnímu projektu. Neposkytuje přístup k formulářům deklarovaným v odkazovaných knihovnách DLL. Chcete-li získat přístup k formuláři, který poskytuje knihovna DLL, je nutné použít kvalifikovaný název formuláře, který je napsán jako *Název_souboru_DLL*. *Formace*.

Vlastnost <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> lze použít k získání kolekce všech otevřených formulářů aplikace.

Objekt a jeho vlastnosti jsou k dispozici pouze pro aplikace systému Windows.

## <a name="properties"></a>Vlastnosti

Každá vlastnost objektu `My.Forms` poskytuje přístup k instanci formuláře v aktuálním projektu. Název vlastnosti je stejný jako název formuláře, ke kterému vlastnost přistupuje, a typ vlastnosti je stejný jako typ formuláře.

> [!NOTE]
> Pokud dojde ke kolizi názvů, název vlastnosti pro přístup k formuláři je *RootNamespace*_*názvový prostor*\_název *formuláře*. Například zvažte dva formuláře s názvem `Form1.`, pokud je jeden z těchto formulářů v kořenovém oboru názvů `WindowsApplication1` a v `Namespace1`oboru názvů, měli byste k tomuto formuláři přistupovat prostřednictvím `My.Forms.WindowsApplication1_Namespace1_Form1`.

Objekt `My.Forms` poskytuje přístup k instanci hlavního formuláře aplikace, který byl vytvořen při spuštění. Pro všechny ostatní formuláře vytvoří objekt `My.Forms` novou instanci formuláře, když je k němu přidaný a uložený. Následné pokusy o přístup k této vlastnosti vrátí tuto instanci formuláře.

Formulář můžete vyřadit přiřazením `Nothing` k vlastnosti tohoto formuláře. Vlastnost setter volá metodu <xref:System.Windows.Forms.Form.Close%2A> formuláře a potom přiřadí `Nothing` uložené hodnotě. Pokud k vlastnosti přiřadíte jinou hodnotu než `Nothing`, vyvolá metoda setter výjimku <xref:System.ArgumentException>.

Můžete otestovat, zda vlastnost objektu `My.Forms` ukládá instanci formuláře pomocí operátoru `Is` nebo `IsNot`. Tyto operátory můžete použít ke kontrole, zda je hodnota vlastnosti `Nothing`.

> [!NOTE]
> Operátor `Is` nebo `IsNot` obvykle musí číst hodnotu vlastnosti pro provedení porovnání. Pokud však vlastnost aktuálně ukládá `Nothing`, vlastnost vytvoří novou instanci formuláře a následně vrátí tuto instanci. Nicméně kompilátor Visual Basic pracuje s vlastnostmi objektu `My.Forms` odlišně a umožňuje operátoru `Is` nebo `IsNot` ke kontrole stavu vlastnosti bez změny její hodnoty.

## <a name="example"></a>Příklad

Tento příklad změní název výchozího formuláře `SidebarMenu`.

[!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]

Aby tento příklad fungoval, projekt musí mít formulář s názvem `SidebarMenu`.

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

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [Objekty](../../../visual-basic/language-reference/objects/index.md)
- [Operátor Is](../../../visual-basic/language-reference/operators/is-operator.md)
- [Operátor IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Přístup k formulářům aplikace](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
