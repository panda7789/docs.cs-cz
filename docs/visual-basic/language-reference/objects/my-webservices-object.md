---
title: My.WebServices – objekt
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: 290d025985663bc45fe605a2e9904fc90fb2bc63
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350340"
---
# <a name="mywebservices-object"></a>My.WebServices – objekt
Poskytuje vlastnosti pro vytvoření a přístup k jedné instanci každé webové služby XML, na kterou odkazuje aktuální projekt.  
  
## <a name="remarks"></a>Poznámky  
 Objekt `My.WebServices` poskytuje instanci každé webové služby, na kterou odkazuje aktuální projekt. Každá instance je vytvořena na vyžádání. K těmto webovým službám můžete přistupovat prostřednictvím vlastností objektu `My.WebServices`. Název vlastnosti je stejný jako název webové služby, ke které vlastnost přistupuje. Libovolná třída, která dědí z <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> je webová služba. Informace o tom, jak přidat webové služby do projektu, najdete v tématu [přístup k aplikačním webovým službám](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Objekt `My.WebServices` zveřejňuje pouze webové služby přidružené k aktuálnímu projektu. Neposkytuje přístup k webovým službám deklarovaným v odkazovaných knihovnách DLL. Chcete-li získat přístup k webové službě, kterou poskytuje knihovna DLL, je nutné použít kvalifikovaný název webové služby ve formě *Název_souboru_DLL*. *Služba WebService*. Další informace najdete v tématu [přístup k aplikačním webovým službám](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Objekt a jeho vlastnosti nejsou k dispozici pro webové aplikace.  
  
## <a name="properties"></a>Vlastnosti  
 Každá vlastnost objektu `My.WebServices` poskytuje přístup k instanci webové služby, na kterou odkazuje aktuální projekt. Název vlastnosti je stejný jako název webové služby, ke které vlastnost přistupuje, a typ vlastnosti je stejný jako typ webové služby.  
  
> [!NOTE]
> Pokud dojde ke kolizi názvů, název vlastnosti pro přístup k webové službě je *RootNamespace*_*názvový prostor*\_*ServiceName*. Zvažte například dvě webové služby s názvem `Service1`. Pokud se jedna z těchto služeb nachází v kořenovém oboru názvů `WindowsApplication1` a v `Namespace1`oboru názvů, měli byste k této službě přistupovat pomocí `My.WebServices.WindowsApplication1_Namespace1_Service1`.  
  
 Když poprvé přistupujete k jedné z vlastností `My.WebServices` objektu, vytvoří se nová instance webové služby a uloží se do ní. Následné přístupy této vlastnosti vrátí tuto instanci webové služby.  
  
 Webovou službu můžete vyřadit tak, že přiřadíte `Nothing` k vlastnosti této webové služby. Vlastnost setter přiřadí `Nothing` k uložené hodnotě. Pokud k vlastnosti přiřadíte jinou hodnotu než `Nothing`, vyvolá metoda setter výjimku <xref:System.ArgumentException>.  
  
 Můžete otestovat, zda vlastnost objektu `My.WebServices` ukládá instanci webové služby pomocí operátoru `Is` nebo `IsNot`. Tyto operátory můžete použít ke kontrole, zda je hodnota vlastnosti `Nothing`.  
  
> [!NOTE]
> Operátor `Is` nebo `IsNot` obvykle musí číst hodnotu vlastnosti pro provedení porovnání. Pokud však vlastnost aktuálně ukládá `Nothing`, vlastnost vytvoří novou instanci webové služby a poté tuto instanci vrátí. Nicméně kompilátor Visual Basic zpracovává vlastnosti objektu `My.WebServices` a umožňuje operátoru `Is` nebo `IsNot` ke kontrole stavu vlastnosti bez změny její hodnoty.  
  
## <a name="example"></a>Příklad  
 Tento příklad volá metodu `FahrenheitToCelsius` webové služby `TemperatureConverter` XML a vrátí výsledek.  
  
 [!code-vb[VbVbalrMyWebService#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWebService/VB/Form1.vb#1)]  
  
 Aby tento příklad fungoval, musí mít projekt odkaz na webovou službu s názvem `Converter`a tato webová služba musí vystavit `ConvertTemperature` metodu. Další informace najdete v tématu [přístup k aplikačním webovým službám](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md).  
  
 Tento kód nefunguje v projektu webové aplikace.  
  
## <a name="requirements"></a>Požadavky  
  
### <a name="availability-by-project-type"></a>Dostupnost podle typu projektu  
  
|Typ projektu|K dispozici|  
|---|---|  
|Aplikace systému Windows|**Ano**|  
|Knihovna tříd|**Ano**|  
|Konzolová aplikace|**Ano**|  
|Knihovna ovládacích prvků Windows|**Ano**|  
|Knihovna webového ovládacího prvku|**Ano**|  
|Služba systému Windows|**Ano**|  
|Web|Ne|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>
- <xref:System.ArgumentException>
- [Přístup k aplikačním webovým službám](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
