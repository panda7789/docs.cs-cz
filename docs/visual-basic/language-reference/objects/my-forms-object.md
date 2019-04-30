---
title: My.Forms – objekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 4998097b910a504461a34af3cc159ddb1c74cc62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949315"
---
# <a name="myforms-object"></a>My.Forms – objekt
Poskytuje vlastnosti pro přístup k instanci jednotlivých formulářů Windows deklarované v aktuálním projektu.  
  
## <a name="remarks"></a>Poznámky  
 `My.Forms` Objekt, který poskytuje instance každý formulář v nástrojích pro aktuální projekt. Název vlastnosti je stejný jako název formuláře, který přistupuje k vlastnosti.   
  
 Dostanete formuláře nabízené modulem `My.Forms` s použitím jméno ve tvaru, bez kvalifikace. Název vlastnosti je stejný jako název typu formuláře, to umožňuje přístup do formuláře, jako kdyby byla výchozí instanci. Například `My.Forms.Form1.Show` je ekvivalentní `Form1.Show`.  
  
 `My.Forms` Zpřístupňuje pouze formuláře, které jsou přidružené k aktuálnímu projektu. Neposkytuje přístup k formulářům deklarované v odkazované knihovny DLL. Pro přístup k formuláře, který obsahuje knihovnu DLL, musíte použít kvalifikovaný název v podobě, zapsán jako *názevsouboru*. *FormName*.  
  
 Můžete použít <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> vlastnost získat kolekci formulářů otevřít všechny aplikace.  
  
 Objekt a její vlastnosti jsou k dispozici pouze pro aplikace Windows.  
  
## <a name="properties"></a>Vlastnosti  
 Každou vlastnost `My.Forms` objekt, který poskytuje přístup k instanci formulář v nástrojích pro aktuální projekt. Název vlastnosti je stejný jako název formuláře, který přistupuje k vlastnosti, a typ vlastnosti je stejný jako typ formuláře.  
  
> [!NOTE]
>  Pokud je kolize názvů, název vlastnosti pro přístup k formuláři je *RootNamespace*_*Namespace*\_*FormName*. Představte si třeba dvě formy s názvem `Form1.`-li jednu z těchto forem, je v kořenovém oboru názvů `WindowsApplication1` a v oboru názvů `Namespace1`, můžete k, které tvoří prostřednictvím `My.Forms.WindowsApplication1_Namespace1_Form1`.  
  
 `My.Forms` Objekt, který poskytuje přístup k instanci aplikace hlavního formuláře, který byl vytvořen při spuštění. Pro všechny ostatní způsoby `My.Forms` objekt vytvoří novou instanci formuláře, když přistupuje a uloží jej. Následné pokusy o přístup k této vlastnosti vrácení této instance formuláře.  
  
 Můžete uvolnit formuláře přiřazením `Nothing` na vlastnost pro daný formulář. Volání metody setter vlastnosti <xref:System.Windows.Forms.Form.Close%2A> metoda formulář, a poté přiřadí `Nothing` k uložené hodnotě. Pokud přiřadíte libovolnou hodnotu jiné než `Nothing` na vlastnost, vyvolá metoda setter <xref:System.ArgumentException> výjimky.  
  
 Můžete zkontrolovat, jestli vlastnost `My.Forms` ukládá instance formulář pomocí `Is` nebo `IsNot` operátor. Chcete-li zkontrolovat, zda je hodnota vlastnosti můžete použít tyto operátory `Nothing`.  
  
> [!NOTE]
>  Obvykle `Is` nebo `IsNot` operátor má být přečtena hodnota vlastnosti k provádění porovnání. Nicméně pokud aktuálně uchovává vlastnost `Nothing`, vlastnost vytvoří novou instanci formuláře a vrátí tuto instanci. Však kompilátor jazyka Visual Basic zpracovává vlastnosti `My.Forms` jinak objektu a umožňuje `Is` nebo `IsNot` operátor zkontrolovat stav vlastnost beze změny jeho hodnotu.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu změní název výchozí `SidebarMenu` formuláře.  
  
 [!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]  
  
 Pro tento příklad fungoval, musí mít váš projekt formulář s názvem `SidebarMenu`.  
  
 Tento kód bude fungovat pouze v projektu aplikace Windows.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="availability-by-project-type"></a>Dostupnost podle typu projektu  
  
|Typ projektu|K dispozici|  
|---|---|  
|Aplikace Windows|**Ano**|  
|Knihovna tříd|Ne|  
|Konzolová aplikace|Ne|  
|Knihovna ovládacích prvků Windows|Ne|  
|Knihovna webových prvků|Ne|  
|Služba systému Windows|Ne|  
|Webové stránky|Ne|  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [Objekty](../../../visual-basic/language-reference/objects/index.md)
- [Operátor Is](../../../visual-basic/language-reference/operators/is-operator.md)
- [Operátor IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Přístup k formulářům aplikace](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
