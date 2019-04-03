---
title: My.WebServices – objekt (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: a60f32c4f581e42f240fca55ce496776c5511ba3
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840429"
---
# <a name="mywebservices-object"></a>My.WebServices – objekt
Poskytuje vlastnosti pro vytváření a přístup ke jednu instanci každé webové služby XML odkazuje aktuální projekt.  
  
## <a name="remarks"></a>Poznámky  
 `My.WebServices` Objekt, který poskytuje instance každou webovou službu odkazuje aktuální projekt. Každá instance je vytvořena na vyžádání. Můžete k těmto webovým službám prostřednictvím vlastnosti `My.WebServices` objektu. Název vlastnosti je stejný jako název webové služby, který přistupuje k vlastnosti. Všechny třídy, která dědí z <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> je webová služba. Informace o přidání do projektu webové služby najdete v tématu [přístup k aplikačním webovým službám](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 `My.WebServices` Zpřístupňuje pouze webové služby přidružené k aktuálnímu projektu. Neposkytuje přístup k webovým službám, které jsou deklarované v odkazované knihovny DLL. Pro přístup k webové službě, která poskytuje knihovnu DLL, je nutné použít kvalifikovaný název webové služby ve formě *názevsouboru*. *WebServiceName*. Další informace najdete v tématu [přístup k aplikačním webovým službám](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Objekt a jeho vlastnosti nejsou k dispozici pro webové aplikace.  
  
## <a name="properties"></a>Vlastnosti  
 Každou vlastnost `My.WebServices` objekt, který poskytuje přístup k instanci webové služby odkazuje aktuální projekt. Název vlastnosti je stejný jako název webové služby, který přistupuje k vlastnosti, a typ vlastnosti je stejný jako typ webové služby.  
  
> [!NOTE]
>  Pokud je kolize názvů, název vlastnosti pro přístup k webové službě je *RootNamespace*_*Namespace*\_*ServiceName*. Představte si třeba dvě webové služby s názvem `Service1`. Pokud jeden z těchto služeb se v kořenovém oboru názvů `WindowsApplication1` a v oboru názvů `Namespace1`, můžete tuto službu k pomocí `My.WebServices.WindowsApplication1_Namespace1_Service1`.  
  
 Při prvním přístupu jeden z `My.WebServices` vlastností objektu ji vytvoří novou instanci webové služby a uloží jej. Následující přístupy do této vlastnosti vrátit tuto instanci webové služby.  
  
 Můžete uvolnit webové služby pomocí přiřazení `Nothing` vlastnosti pro tuto webovou službu. Metoda setter vlastnosti přiřadí `Nothing` k uložené hodnotě. Pokud přiřadíte libovolnou hodnotu jiné než `Nothing` na vlastnost, vyvolá metoda setter <xref:System.ArgumentException> výjimky.  
  
 Můžete zkontrolovat, jestli vlastnost `My.WebServices` ukládá instance webové služby pomocí `Is` nebo `IsNot` operátor. Chcete-li zkontrolovat, zda je hodnota vlastnosti můžete použít tyto operátory `Nothing`.  
  
> [!NOTE]
>  Obvykle `Is` nebo `IsNot` operátor má být přečtena hodnota vlastnosti k provádění porovnání. Nicméně pokud aktuálně uchovává vlastnost `Nothing`, vlastnost vytvoří novou instanci webové služby a vrátí tuto instanci. Však kompilátor jazyka Visual Basic zpracovává vlastnosti `My.WebServices` speciálně objektu a umožňuje `Is` nebo `IsNot` operátor zkontrolovat stav vlastnost beze změny jeho hodnotu.  
  
## <a name="example"></a>Příklad  
 Tento příklad příkladu volá `FahrenheitToCelsius` metodu `TemperatureConverter` webové služby XML a vrátí výsledek.  
  
 [!code-vb[VbVbalrMyWebService#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWebService/VB/Form1.vb#1)]  
  
 Pro tento příklad fungoval, musí váš projekt odkazovat webové služby s názvem `Converter`, a musí zveřejnit této webové služby `ConvertTemperature` metody. Další informace najdete v tématu [přístup k aplikačním webovým službám](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Tento kód nefunguje v projektu webové aplikace.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="availability-by-project-type"></a>Dostupnost podle typu projektu  
  
|Typ projektu|K dispozici|  
|---|---|  
|Aplikace Windows|**Ano**|  
|Knihovna tříd|**Ano**|  
|Konzolová aplikace|**Ano**|  
|Knihovna ovládacích prvků Windows|**Ano**|  
|Knihovna webových prvků|**Ano**|  
|Služba systému Windows|**Ano**|  
|Webové stránky|Ne|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>
- <xref:System.ArgumentException>
- [Přístup k aplikačním webovým službám](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
