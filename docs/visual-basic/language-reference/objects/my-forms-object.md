---
title: "My.Forms – objekt"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords: My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fe548caacf2c8e7498e3b7abc814b4f89af9b3d6
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="myforms-object"></a>My.Forms – objekt
Poskytuje vlastnosti pro přístup k instanci jednotlivých formulářů Windows, které jsou deklarované v aktuálním projektu.  
  
## <a name="remarks"></a>Poznámky  
 `My.Forms` Objekt poskytuje instanci každého formuláře v aktuálním projektu. Název vlastnosti je stejný jako název ve tvaru, který přistupuje k vlastnosti.   
  
 Dostanete formulářích, které `My.Forms` objektu pomocí názvu formuláře, bez kvalifikace. Název vlastnosti je stejný jako název typu formuláře, to umožňuje přístup do formuláře jako, pokud má výchozí instance. Například `My.Forms.Form1.Show` je ekvivalentní `Form1.Show`.  
  
 `My.Forms` Objekt se poskytuje pouze formuláře, které jsou přidružené k aktuální projekt. Neposkytuje přístup k formulářům deklarované v odkazované knihovny DLL. Pro přístup k formuláři, který knihovny DLL, musíte použít kvalifikovaný název ve tvaru, zapisují jako *názevsouboru*. *Položky název formuláře*.  
  
 Můžete použít <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> vlastnost k získání kolekce otevřených formulářů všechny aplikace.  
  
 Objekt a jeho vlastnosti jsou k dispozici pouze pro aplikace systému Windows.  
  
## <a name="properties"></a>Vlastnosti  
 Každou vlastnost `My.Forms` objekt poskytuje přístup k instanci formuláře v aktuálním projektu. Název vlastnosti je stejný jako název ve tvaru, který přistupuje k vlastnosti a typ vlastnosti je stejný jako typ formuláře.  
  
> [!NOTE]
>  Pokud je kolize názvů, název vlastnosti pro přístup k formuláři je *RootNamespace*_*Namespace*\_*položky název formuláře*. Představte si třeba dva formuláře s názvem `Form1.`Pokud jeden z těchto formulářů je v oboru názvů kořenové `WindowsApplication1` a v oboru názvů `Namespace1`, by přístup Tato forma prostřednictvím `My.Forms.WindowsApplication1_Namespace1_Form1`.  
  
 `My.Forms` Objekt poskytuje přístup k instanci aplikace hlavní formulář, který byl vytvořen při spuštění. Pro všechny ostatní způsoby `My.Forms` objekt vytvoří novou instanci formuláře při přístupu k a uloží ji. Následné pokusy o přístup k vlastnosti vrátí tuto instanci formuláře.  
  
 Můžete vyřazení formuláře přiřazením `Nothing` pro vlastnost pro daný formulář. Vlastnost setter volání <xref:System.Windows.Forms.Form.Close%2A> metoda formuláře, a poté přiřadí `Nothing` uložené hodnotě. Chcete-li přiřadit žádnou hodnotu než `Nothing` pro vlastnost, nastavovací metoda vyvolá <xref:System.ArgumentException> výjimka.  
  
 Můžete zkontrolovat, zda vlastnost `My.Forms` objekt ukládá instance formuláře pomocí `Is` nebo `IsNot` operátor. Tyto operátory můžete zkontrolovat, zda je hodnota vlastnosti `Nothing`.  
  
> [!NOTE]
>  Obvykle `Is` nebo `IsNot` operátor má načíst hodnotu vlastnosti, která má-li provést porovnání. Ale pokud vlastnost aktuálně ukládá `Nothing`, vlastnost vytvoří novou instanci třídy formuláře a vrátí tuto instanci. Ale Visual Basic – kompilátor zpracovává vlastnosti `My.Forms` objektu jinak a umožňuje `Is` nebo `IsNot` operátor a zkontrolujte stav vlastnosti beze změny jeho hodnotu.  
  
## <a name="example"></a>Příklad  
 Tento příklad změní název výchozí `SidebarMenu` formuláře.  
  
 [!code-vb[VbVbalrMyForms#2](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-forms-object_1.vb)]  
  
 Pro tento příklad fungoval, musí mít váš projekt formuláře s názvem `SidebarMenu`.  
  
 Tento kód bude fungovat pouze v projektu aplikace systému Windows.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="availability-by-project-type"></a>Dostupnost podle typu projektu  
  
|Typ projektu|K dispozici|  
|---|---|  
|Aplikace systému Windows|**Ano**|  
|Knihovna tříd|Ne|  
|Konzolová aplikace|Ne|  
|Knihovna ovládacích prvků Windows|Ne|  
|Knihovna webových prvků|Ne|  
|Služba systému Windows|Ne|  
|Webový server|Ne|  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Form.Close%2A>  
 [Objekty](../../../visual-basic/language-reference/objects/index.md)  
 [Operátor Is](../../../visual-basic/language-reference/operators/is-operator.md)  
 [Operátor IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Přístup k formulářům aplikace](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
