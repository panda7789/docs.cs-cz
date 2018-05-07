---
title: My.WebServices – objekt
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: 9519638c7609b9b1d0f5e07397c46975e2696c94
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="mywebservices-object"></a>My.WebServices – objekt
Poskytuje vlastnosti pro vytváření a přístup k jediné instance každého XML webové služby odkazuje v aktuálním projektu.  
  
## <a name="remarks"></a>Poznámky  
 `My.WebServices` Objekt poskytuje instanci každé webové služby odkazuje v aktuálním projektu. Každá instance je vytvořena na vyžádání. Tyto webové služby můžete přistupovat prostřednictvím vlastnosti `My.WebServices` objektu. Název vlastnosti je stejný jako název webové služby, který má přístup k vlastnosti. Všechny třídy, která dědí z <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> je webová služba. Informace o přidání do projektu webové služby najdete v tématu [přístup k aplikačním webovým službám](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 `My.WebServices` Objekt se poskytuje pouze webové služby přidružené k aktuální projekt. Neposkytuje přístup k webovým službám, které jsou deklarované v odkazované knihovny DLL. Pro přístup k webové službě, která poskytuje knihovnu DLL, musíte použít kvalifikovaný název webové služby, ve tvaru *názevsouboru*. *WebServiceName*. Další informace najdete v tématu [přístup k aplikačním webovým službám](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Objekt a jeho vlastnosti nejsou k dispozici pro webové aplikace.  
  
## <a name="properties"></a>Vlastnosti  
 Každou vlastnost `My.WebServices` objekt poskytuje přístup k instanci webové služby odkazuje v aktuálním projektu. Název vlastnosti je stejný jako název webové služby, který má přístup k vlastnosti a typ vlastnosti je stejný jako typ webovou službu.  
  
> [!NOTE]
>  Pokud je kolize názvů, je název vlastnosti pro přístup k webové službě *RootNamespace*_*Namespace*\_*ServiceName*. Představte si třeba dva webové služby s názvem `Service1`. Pokud jeden z těchto služeb je v kořenovém oboru názvů `WindowsApplication1` a v oboru názvů `Namespace1`, bude přístup k této službě pomocí `My.WebServices.WindowsApplication1_Namespace1_Service1`.  
  
 Pokud nejprve přístup mezi `My.WebServices` vlastností objektu vytvoří novou instanci třídy webové služby a uloží ji. Následných přístupech této vlastnosti vrátí tuto instanci webové služby.  
  
 Můžete vyřazení webové služby přiřazením `Nothing` vlastnosti pro tuto webovou službu. Metoda setter vlastnosti přiřadí `Nothing` uložené hodnotě. Chcete-li přiřadit žádnou hodnotu než `Nothing` pro vlastnost, nastavovací metoda vyvolá <xref:System.ArgumentException> výjimka.  
  
 Můžete zkontrolovat, zda vlastnost `My.WebServices` objekt ukládá instance webové služby pomocí `Is` nebo `IsNot` operátor. Tyto operátory můžete zkontrolovat, zda je hodnota vlastnosti `Nothing`.  
  
> [!NOTE]
>  Obvykle `Is` nebo `IsNot` operátor má načíst hodnotu vlastnosti, která má-li provést porovnání. Ale pokud vlastnost aktuálně ukládá `Nothing`, vlastnost vytvoří novou instanci webové služby a vrátí tuto instanci. Ale Visual Basic – kompilátor zpracovává vlastnosti `My.WebServices` speciálně objektu a umožňuje `Is` nebo `IsNot` operátor a zkontrolujte stav vlastnosti beze změny jeho hodnotu.  
  
## <a name="example"></a>Příklad  
 Tento příklad volá `FahrenheitToCelsius` metodu `TemperatureConverter` XML webové služby a vrátí výsledek.  
  
 [!code-vb[VbVbalrMyWebService#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-webservices-object_1.vb)]  
  
 Pro tento příklad fungoval, musí odkazovat projektu webové služby s názvem `Converter`, a že webové služby musí vystavit `ConvertTemperature` metoda. Další informace najdete v tématu [přístup k aplikačním webovým službám](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Tento kód nefunguje v projektu webové aplikace.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="availability-by-project-type"></a>Dostupnost podle typu projektu  
  
|Typ projektu|K dispozici|  
|---|---|  
|Aplikace systému Windows|**Ano**|  
|Knihovna tříd|**Ano**|  
|Konzolová aplikace|**Ano**|  
|Knihovna ovládacích prvků Windows|**Ano**|  
|Knihovna webových prvků|**Ano**|  
|Služba systému Windows|**Ano**|  
|Webový server|Ne|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>  
 <xref:System.ArgumentException>  
 [Přístup k aplikačním webovým službám](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
