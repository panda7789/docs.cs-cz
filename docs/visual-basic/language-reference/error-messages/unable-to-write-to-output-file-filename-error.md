---
title: 'Nelze zapisovat do výstupního souboru &#39; &lt;filename&gt;&#39;: &lt;chyba&gt;'
ms.date: 07/20/2015
f1_keywords:
- vbc31019
- bc31019
helpviewer_keywords:
- BC31019
ms.assetid: 0845b245-11bb-46fd-95ca-f6cef3c318ef
ms.openlocfilehash: e8fbfd54782e601595712035827ea346d1dbf500
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597507"
---
# <a name="unable-to-write-to-output-file-39ltfilenamegt39-lterrorgt"></a><span data-ttu-id="48e93-102">Nelze zapisovat do výstupního souboru &#39; &lt;filename&gt;&#39;: &lt;chyba&gt;</span><span class="sxs-lookup"><span data-stu-id="48e93-102">Unable to write to output file &#39;&lt;filename&gt;&#39;: &lt;error&gt;</span></span>
<span data-ttu-id="48e93-103">Došlo k potížím, vytvoření souboru.</span><span class="sxs-lookup"><span data-stu-id="48e93-103">There was a problem creating the file.</span></span>  
  
 <span data-ttu-id="48e93-104">Výstupní soubor nelze otevřít pro zápis.</span><span class="sxs-lookup"><span data-stu-id="48e93-104">An output file cannot be opened for writing.</span></span> <span data-ttu-id="48e93-105">Soubor (nebo ve složce obsahující soubor) můžou být otevřené pro výhradní použití jiný proces, nebo může mít jeho nastaven atribut jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="48e93-105">The file (or the folder containing the file) may be opened for exclusive use by another process, or it may have its read-only attribute set.</span></span>  
  
 <span data-ttu-id="48e93-106">Běžné situace, kdy je výhradně otevřen souboru jsou:</span><span class="sxs-lookup"><span data-stu-id="48e93-106">Common situations where a file is opened exclusively are:</span></span>  
  
-   <span data-ttu-id="48e93-107">Aplikace je již spuštěna a pomocí jeho soubory.</span><span class="sxs-lookup"><span data-stu-id="48e93-107">The application is already running and using its files.</span></span> <span data-ttu-id="48e93-108">Chcete-li tento problém vyřešit, ujistěte se, že aplikace není spuštěn.</span><span class="sxs-lookup"><span data-stu-id="48e93-108">To solve this problem, make sure that the application is not running.</span></span>  
  
-   <span data-ttu-id="48e93-109">Jiná aplikace má otevřít soubor.</span><span class="sxs-lookup"><span data-stu-id="48e93-109">Another application has opened the file.</span></span> <span data-ttu-id="48e93-110">Chcete-li tento problém vyřešit, ujistěte se, že žádná jiná aplikace, je přístup k souborům.</span><span class="sxs-lookup"><span data-stu-id="48e93-110">To solve this problem, make sure that no other application is accessing the files.</span></span> <span data-ttu-id="48e93-111">Není vždy zřejmé aplikaci, pro kterou je přístupu k souborům; restartování počítače v takovém případě může být nejjednodušší způsob, jak aplikaci ukončit.</span><span class="sxs-lookup"><span data-stu-id="48e93-111">It is not always obvious which application is accessing your files; in that case, restarting the computer might be the easiest way to terminate the application.</span></span>  
  
 <span data-ttu-id="48e93-112">Pokud ani jeden z výstupních souborů projektu je označena jako jen pro čtení, bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="48e93-112">If even one of the project output files is marked as read-only, this exception will be thrown.</span></span>  
  
 <span data-ttu-id="48e93-113">**ID chyby:** BC31019</span><span class="sxs-lookup"><span data-stu-id="48e93-113">**Error ID:** BC31019</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="48e93-114">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="48e93-114">To correct this error</span></span>  
  
1.  <span data-ttu-id="48e93-115">Kompilace programu zjistíte, pokud se chyba objeví znovu.</span><span class="sxs-lookup"><span data-stu-id="48e93-115">Compile the program again to see if the error recurs.</span></span>  
  
2.  <span data-ttu-id="48e93-116">Pokud potíže potrvají, uložte si práci a restartujte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="48e93-116">If the error continues, save your work and restart Visual Studio.</span></span>  
  
3.  <span data-ttu-id="48e93-117">Pokud potíže potrvají, restartujte počítač.</span><span class="sxs-lookup"><span data-stu-id="48e93-117">If the error continues, restart the computer.</span></span>  
  
4.  <span data-ttu-id="48e93-118">Pokud se chyba objeví znovu, přeinstalujte jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="48e93-118">If the error recurs, reinstall Visual Basic.</span></span>  
  
5.  <span data-ttu-id="48e93-119">Pokud chyba přetrvává i po přeinstalování, upozorněte služby Microsoft Product Support Services.</span><span class="sxs-lookup"><span data-stu-id="48e93-119">If the error persists after reinstallation, notify Microsoft Product Support Services.</span></span>  
  
### <a name="to-check-file-attributes-in-file-explorer"></a><span data-ttu-id="48e93-120">Chcete-li zkontrolovat atributů souboru v Průzkumníkovi souborů</span><span class="sxs-lookup"><span data-stu-id="48e93-120">To check file attributes in File Explorer</span></span>  
  
1.  <span data-ttu-id="48e93-121">Otevřete složku, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="48e93-121">Open the folder you are interested in.</span></span>  
  
2.  <span data-ttu-id="48e93-122">Klikněte **zobrazení** ikonu a vyberte **podrobnosti**.</span><span class="sxs-lookup"><span data-stu-id="48e93-122">Click the **Views** icon and choose **Details**.</span></span>  
  
3.  <span data-ttu-id="48e93-123">Klikněte pravým tlačítkem myši na záhlaví sloupce a vyberte **atributy** z rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="48e93-123">Right-click the column header, and choose **Attributes** from the drop-down list.</span></span>  
  
### <a name="to-change-the-attributes-of-a-file-or-folder"></a><span data-ttu-id="48e93-124">Chcete-li změnit atributy souboru nebo složky</span><span class="sxs-lookup"><span data-stu-id="48e93-124">To change the attributes of a file or folder</span></span>  
  
1.  <span data-ttu-id="48e93-125">V **Průzkumníka souborů**, klikněte pravým tlačítkem na soubor nebo složku a vyberte možnost **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="48e93-125">In **File Explorer**, right-click the file or folder and choose **Properties**.</span></span>  
  
2.  <span data-ttu-id="48e93-126">V **atributy** části **Obecné** zrušte **jen pro čtení** pole.</span><span class="sxs-lookup"><span data-stu-id="48e93-126">In the **Attributes** section of the **General** tab, clear the **Read-only** box.</span></span>  
  
3.  <span data-ttu-id="48e93-127">Press **OK**.</span><span class="sxs-lookup"><span data-stu-id="48e93-127">Press **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48e93-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="48e93-128">See Also</span></span>  
 [<span data-ttu-id="48e93-129">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="48e93-129">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
