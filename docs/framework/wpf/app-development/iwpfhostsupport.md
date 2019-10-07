---
title: IWpfHostSupport
ms.date: 03/30/2017
helpviewer_keywords:
- IWpfHostSupport interface [WPF]
ms.assetid: cc5a0281-de81-4cc1-87e4-0e46b1a811e9
ms.openlocfilehash: 85309e46403b2f22f9afb760d4c4ae370c39246b
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004091"
---
# <a name="iwpfhostsupport"></a>IWpfHostSupport
Aplikace, které hostují obsah [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] prostřednictvím PresentationHost. exe implementují toto rozhraní, aby poskytovaly bod integrace mezi hostitelem a PresentationHost. exe.  
  
## <a name="remarks"></a>Poznámky  
 @no__t – 0 aplikace, jako jsou například webové prohlížeče, mohou hostovat obsah WPF, včetně [!INCLUDE[TLA#tla_xbap#plural](../../../../includes/tlasharptla-xbapsharpplural-md.md)] a volného kódu XAML. Pro hostování obsahu WPF aplikace [!INCLUDE[TLA#tla_win32](../../../../includes/tlasharptla-win32-md.md)] vytvoří instanci [ovládacího prvku WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911). Aby bylo možné hostovat, WPF vytvoří instanci PresentationHost. exe, která poskytne hostovanému obsahu WPF na hostitele pro zobrazení v [ovládacím prvku WebBrowser](https://go.microsoft.com/fwlink/?LinkId=97911).  
  
 Integrace povolená pomocí `IWpfHostSupport` umožňuje PresentationHost. exe:  
  
- Vyhledejte a zaregistrujte se nezpracovanými vstupními zařízeními (zařízení s lidskými rozhraními), na které má hostitelská aplikace zájem.  
  
- Přijímat vstupní zprávy z registrovaných nezpracovaných vstupních zařízení a předají příslušné zprávy do hostitelské aplikace.  
  
- Dotazování hostitelské aplikace na vlastní průběh a chybná uživatelská rozhraní.  
  
> [!NOTE]
> Toto rozhraní API je zamýšlené a podporované jenom pro použití v místním klientském počítači.  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|[GetRawInputDevices](getrawinputdevices.md)|Umožňuje PresentationHost. exe zjistit nezpracované vstupní zařízení (zařízení s lidskými rozhraními), na které hostitelská aplikace zajímá.|  
|[FilterInputMessage](filterinputmessage.md)|Volá se PresentationHost. exe, když se přijme zpráva, pokud se nevrátí E_NOTIMPL.|  
|[GetCustomUI](getcustomui.md)|Ve výchozím nastavení poskytuje PresentationHost. exe vlastní průběh nasazení a uživatelská rozhraní chyby nasazení, která se zobrazí při nasazení obsahu WPF.|
