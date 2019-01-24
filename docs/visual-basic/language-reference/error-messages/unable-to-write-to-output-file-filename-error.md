---
title: 'Nelze zapisovat do výstupního souboru &#39; &lt;filename&gt;&#39;: &lt;chyba&gt;'
ms.date: 07/20/2015
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
ms.openlocfilehash: c82f1e6e4a01af87cc7dce49cfaa78f9be1631db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572692"
---
# <a name="unable-to-write-to-output-file-39ltfilenamegt39-lterrorgt"></a><span data-ttu-id="fd078-102">Nelze zapisovat do výstupního souboru &#39; &lt;filename&gt;&#39;: &lt;chyba&gt;</span><span class="sxs-lookup"><span data-stu-id="fd078-102">Unable to write to output file &#39;&lt;filename&gt;&#39;: &lt;error&gt;</span></span>
<span data-ttu-id="fd078-103">Došlo k potížím, vytváření souboru.</span><span class="sxs-lookup"><span data-stu-id="fd078-103">There was a problem creating the file.</span></span>  
  
 <span data-ttu-id="fd078-104">Výstupní soubor nelze otevřít pro zápis.</span><span class="sxs-lookup"><span data-stu-id="fd078-104">An output file cannot be opened for writing.</span></span> <span data-ttu-id="fd078-105">Soubor (nebo na složku obsahující soubor) můžou být otevřené pro výhradní použití jiným procesem nebo je možné, že jeho nastaven atribut jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="fd078-105">The file (or the folder containing the file) may be opened for exclusive use by another process, or it may have its read-only attribute set.</span></span>  
  
 <span data-ttu-id="fd078-106">Běžné situace, kde je soubor otevřený výhradně jsou:</span><span class="sxs-lookup"><span data-stu-id="fd078-106">Common situations where a file is opened exclusively are:</span></span>  
  
-   <span data-ttu-id="fd078-107">Aplikace je již spuštěn a pomocí jeho soubory.</span><span class="sxs-lookup"><span data-stu-id="fd078-107">The application is already running and using its files.</span></span> <span data-ttu-id="fd078-108">Chcete-li tento problém vyřešit, ujistěte se, že aplikace není spuštěna.</span><span class="sxs-lookup"><span data-stu-id="fd078-108">To solve this problem, make sure that the application is not running.</span></span>  
  
-   <span data-ttu-id="fd078-109">Jiná aplikace má soubor otevřen.</span><span class="sxs-lookup"><span data-stu-id="fd078-109">Another application has opened the file.</span></span> <span data-ttu-id="fd078-110">Chcete-li tento problém vyřešit, ujistěte se, že žádná jiná aplikace je přístup k souborům.</span><span class="sxs-lookup"><span data-stu-id="fd078-110">To solve this problem, make sure that no other application is accessing the files.</span></span> <span data-ttu-id="fd078-111">Není vždy zřejmé aplikaci, pro kterou je přístupu k souborům; restartování počítače v takovém případě může být nejjednodušší způsob, jak aplikaci ukončit.</span><span class="sxs-lookup"><span data-stu-id="fd078-111">It is not always obvious which application is accessing your files; in that case, restarting the computer might be the easiest way to terminate the application.</span></span>  
  
 <span data-ttu-id="fd078-112">Pokud ani jeden z výstupních souborů projektu je označena jako jen pro čtení, tato výjimka bude vyvolána.</span><span class="sxs-lookup"><span data-stu-id="fd078-112">If even one of the project output files is marked as read-only, this exception will be thrown.</span></span>  
  
 <span data-ttu-id="fd078-113">**ID chyby:** BC31019</span><span class="sxs-lookup"><span data-stu-id="fd078-113">**Error ID:** BC31019</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fd078-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="fd078-114">To correct this error</span></span>  
  
1.  <span data-ttu-id="fd078-115">Kompilovat program znovu, abyste viděli, pokud se chyba objeví znovu.</span><span class="sxs-lookup"><span data-stu-id="fd078-115">Compile the program again to see if the error recurs.</span></span>  
  
2.  <span data-ttu-id="fd078-116">Pokud chyba přetrvává, uložte si práci a restartujte aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fd078-116">If the error continues, save your work and restart Visual Studio.</span></span>  
  
3.  <span data-ttu-id="fd078-117">Pokud chyba přetrvává, restartujte počítač.</span><span class="sxs-lookup"><span data-stu-id="fd078-117">If the error continues, restart the computer.</span></span>  
  
4.  <span data-ttu-id="fd078-118">Pokud se chyba objeví znovu, přeinstalujte Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fd078-118">If the error recurs, reinstall Visual Basic.</span></span>  
  
5.  <span data-ttu-id="fd078-119">Pokud chyba přetrvává po přeinstalaci, upozorní Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="fd078-119">If the error persists after reinstallation, notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-check-file-attributes-in-file-explorer"></a><span data-ttu-id="fd078-120">Ke kontrole atributů souboru v Průzkumníku souborů</span><span class="sxs-lookup"><span data-stu-id="fd078-120">To check file attributes in File Explorer</span></span>  
  
1.  <span data-ttu-id="fd078-121">Otevřete složku, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="fd078-121">Open the folder you are interested in.</span></span>  
  
2.  <span data-ttu-id="fd078-122">Klikněte na tlačítko **zobrazení** ikonu a zvolte **podrobnosti**.</span><span class="sxs-lookup"><span data-stu-id="fd078-122">Click the **Views** icon and choose **Details**.</span></span>  
  
3.  <span data-ttu-id="fd078-123">Klikněte pravým tlačítkem na záhlaví sloupce a vybrat **atributy** z rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="fd078-123">Right-click the column header, and choose **Attributes** from the drop-down list.</span></span>  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a><span data-ttu-id="fd078-124">Chcete-li změnit atributy souboru nebo složky</span><span class="sxs-lookup"><span data-stu-id="fd078-124">To change the attributes of a file or folder</span></span>  
  
1.  <span data-ttu-id="fd078-125">V **Průzkumníka souborů**, klikněte pravým tlačítkem na soubor nebo složku a zvolte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="fd078-125">In **File Explorer**, right-click the file or folder and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="fd078-126">V **atributy** část **Obecné** kartu, zrušte **jen pro čtení** pole.</span><span class="sxs-lookup"><span data-stu-id="fd078-126">In the **Attributes** section of the **General** tab, clear the **Read-only** box.</span></span>  
  
3.  <span data-ttu-id="fd078-127">Stisknutím klávesy **OK**.</span><span class="sxs-lookup"><span data-stu-id="fd078-127">Press **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd078-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd078-128">See also</span></span>
- [<span data-ttu-id="fd078-129">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="fd078-129">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
