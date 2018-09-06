---
title: Kolekce schémat ODBC
ms.date: 03/30/2017
ms.assetid: 1bb126a5-ceec-4649-a4bc-8aa19e801046
ms.openlocfilehash: bdedbb11960f02b99dcca6388abf663635238f74
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43750006"
---
# <a name="odbc-schema-collections"></a><span data-ttu-id="524a5-102">Kolekce schémat ODBC</span><span class="sxs-lookup"><span data-stu-id="524a5-102">ODBC Schema Collections</span></span>
<span data-ttu-id="524a5-103">Tato část popisuje kolekci podpora schématu pro ovladače ODBC pro Microsoft SQL Server, Oracle a Microsoft Jet.</span><span class="sxs-lookup"><span data-stu-id="524a5-103">This section discusses schema collection support for the ODBC drivers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-odbc-driver"></a><span data-ttu-id="524a5-104">Ovladač ODBC Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="524a5-104">Microsoft SQL Server ODBC Driver</span></span>  
 <span data-ttu-id="524a5-105">Ovladače ODBC Microsoft SQL Server podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="524a5-105">The Microsoft SQL Server ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="524a5-106">Tabulky</span><span class="sxs-lookup"><span data-stu-id="524a5-106">Tables</span></span>  
  
-   <span data-ttu-id="524a5-107">Indexy</span><span class="sxs-lookup"><span data-stu-id="524a5-107">Indexes</span></span>  
  
-   <span data-ttu-id="524a5-108">Sloupce</span><span class="sxs-lookup"><span data-stu-id="524a5-108">Columns</span></span>  
  
-   <span data-ttu-id="524a5-109">Procedury</span><span class="sxs-lookup"><span data-stu-id="524a5-109">Procedures</span></span>  
  
-   <span data-ttu-id="524a5-110">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="524a5-110">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="524a5-111">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="524a5-111">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="524a5-112">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="524a5-112">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="524a5-113">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="524a5-113">Tables and Views</span></span>  
  
|<span data-ttu-id="524a5-114">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="524a5-114">ColumnName</span></span>|<span data-ttu-id="524a5-115">Datový typ</span><span class="sxs-lookup"><span data-stu-id="524a5-115">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="524a5-116">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="524a5-116">TABLE_CAT</span></span>|<span data-ttu-id="524a5-117">String</span><span class="sxs-lookup"><span data-stu-id="524a5-117">String</span></span>|  
|<span data-ttu-id="524a5-118">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="524a5-118">TABLE_SCHEM</span></span>|<span data-ttu-id="524a5-119">String</span><span class="sxs-lookup"><span data-stu-id="524a5-119">String</span></span>|  
|<span data-ttu-id="524a5-120">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-120">TABLE_NAME</span></span>|<span data-ttu-id="524a5-121">String</span><span class="sxs-lookup"><span data-stu-id="524a5-121">String</span></span>|  
|<span data-ttu-id="524a5-122">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-122">TABLE_TYPE</span></span>|<span data-ttu-id="524a5-123">String</span><span class="sxs-lookup"><span data-stu-id="524a5-123">String</span></span>|  
|<span data-ttu-id="524a5-124">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="524a5-124">REMARKS</span></span>|<span data-ttu-id="524a5-125">String</span><span class="sxs-lookup"><span data-stu-id="524a5-125">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="524a5-126">Indexy</span><span class="sxs-lookup"><span data-stu-id="524a5-126">Indexes</span></span>  
  
|<span data-ttu-id="524a5-127">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="524a5-127">ColumnName</span></span>|<span data-ttu-id="524a5-128">Datový typ</span><span class="sxs-lookup"><span data-stu-id="524a5-128">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="524a5-129">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="524a5-129">TABLE_CAT</span></span>|<span data-ttu-id="524a5-130">String</span><span class="sxs-lookup"><span data-stu-id="524a5-130">String</span></span>|  
|<span data-ttu-id="524a5-131">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="524a5-131">TABLE_SCHEM</span></span>|<span data-ttu-id="524a5-132">String</span><span class="sxs-lookup"><span data-stu-id="524a5-132">String</span></span>|  
|<span data-ttu-id="524a5-133">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-133">TABLE_NAME</span></span>|<span data-ttu-id="524a5-134">String</span><span class="sxs-lookup"><span data-stu-id="524a5-134">String</span></span>|  
|<span data-ttu-id="524a5-135">NON_UNIQUE</span><span class="sxs-lookup"><span data-stu-id="524a5-135">NON_UNIQUE</span></span>|<span data-ttu-id="524a5-136">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-136">Int16</span></span>|  
|<span data-ttu-id="524a5-137">INDEX_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="524a5-137">INDEX_QUALIFIER</span></span>|<span data-ttu-id="524a5-138">String</span><span class="sxs-lookup"><span data-stu-id="524a5-138">String</span></span>|  
|<span data-ttu-id="524a5-139">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-139">INDEX_NAME</span></span>|<span data-ttu-id="524a5-140">String</span><span class="sxs-lookup"><span data-stu-id="524a5-140">String</span></span>|  
|<span data-ttu-id="524a5-141">TYP</span><span class="sxs-lookup"><span data-stu-id="524a5-141">TYPE</span></span>|<span data-ttu-id="524a5-142">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-142">Int16</span></span>|  
|<span data-ttu-id="524a5-143">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="524a5-143">ORDINAL_POSITION</span></span>|<span data-ttu-id="524a5-144">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-144">Int16</span></span>|  
|<span data-ttu-id="524a5-145">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-145">COLUMN_NAME</span></span>|<span data-ttu-id="524a5-146">String</span><span class="sxs-lookup"><span data-stu-id="524a5-146">String</span></span>|  
|<span data-ttu-id="524a5-147">ASC_OR_DESC</span><span class="sxs-lookup"><span data-stu-id="524a5-147">ASC_OR_DESC</span></span>|<span data-ttu-id="524a5-148">String</span><span class="sxs-lookup"><span data-stu-id="524a5-148">String</span></span>|  
|<span data-ttu-id="524a5-149">CARDINATLITY</span><span class="sxs-lookup"><span data-stu-id="524a5-149">CARDINATLITY</span></span>|<span data-ttu-id="524a5-150">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-150">Int32</span></span>|  
|<span data-ttu-id="524a5-151">STRÁNKY</span><span class="sxs-lookup"><span data-stu-id="524a5-151">PAGES</span></span>|<span data-ttu-id="524a5-152">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-152">Int32</span></span>|  
|<span data-ttu-id="524a5-153">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="524a5-153">FILTER_CONDITION</span></span>|<span data-ttu-id="524a5-154">String</span><span class="sxs-lookup"><span data-stu-id="524a5-154">String</span></span>|  
|<span data-ttu-id="524a5-155">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="524a5-155">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="524a5-156">String</span><span class="sxs-lookup"><span data-stu-id="524a5-156">String</span></span>|  
|<span data-ttu-id="524a5-157">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-157">SS_DATA_TYPE</span></span>|<span data-ttu-id="524a5-158">Byte</span><span class="sxs-lookup"><span data-stu-id="524a5-158">Byte</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="524a5-159">Sloupce</span><span class="sxs-lookup"><span data-stu-id="524a5-159">Columns</span></span>  
  
|<span data-ttu-id="524a5-160">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="524a5-160">ColumnName</span></span>|<span data-ttu-id="524a5-161">Datový typ</span><span class="sxs-lookup"><span data-stu-id="524a5-161">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="524a5-162">TABLE_CAT</span><span class="sxs-lookup"><span data-stu-id="524a5-162">TABLE_CAT</span></span>|<span data-ttu-id="524a5-163">String</span><span class="sxs-lookup"><span data-stu-id="524a5-163">String</span></span>|  
|<span data-ttu-id="524a5-164">TABLE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="524a5-164">TABLE_SCHEM</span></span>|<span data-ttu-id="524a5-165">String</span><span class="sxs-lookup"><span data-stu-id="524a5-165">String</span></span>|  
|<span data-ttu-id="524a5-166">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-166">TABLE_NAME</span></span>|<span data-ttu-id="524a5-167">String</span><span class="sxs-lookup"><span data-stu-id="524a5-167">String</span></span>|  
|<span data-ttu-id="524a5-168">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-168">COLUMN_NAME</span></span>|<span data-ttu-id="524a5-169">String</span><span class="sxs-lookup"><span data-stu-id="524a5-169">String</span></span>|  
|<span data-ttu-id="524a5-170">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-170">DATA_TYPE</span></span>|<span data-ttu-id="524a5-171">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-171">Int16</span></span>|  
|<span data-ttu-id="524a5-172">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-172">TYPE_NAME</span></span>|<span data-ttu-id="524a5-173">String</span><span class="sxs-lookup"><span data-stu-id="524a5-173">String</span></span>|  
|<span data-ttu-id="524a5-174">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="524a5-174">COLUMN_SIZE</span></span>|<span data-ttu-id="524a5-175">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-175">Int32</span></span>|  
|<span data-ttu-id="524a5-176">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="524a5-176">BUFFER_LENGTH</span></span>|<span data-ttu-id="524a5-177">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-177">Int32</span></span>|  
|<span data-ttu-id="524a5-178">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="524a5-178">DECIMAL_DIGITS</span></span>|<span data-ttu-id="524a5-179">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-179">Int16</span></span>|  
|<span data-ttu-id="524a5-180">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="524a5-180">NUM_PREC_RADIX</span></span>|<span data-ttu-id="524a5-181">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-181">Int16</span></span>|  
|<span data-ttu-id="524a5-182">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="524a5-182">NULLABLE</span></span>|<span data-ttu-id="524a5-183">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-183">Int16</span></span>|  
|<span data-ttu-id="524a5-184">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="524a5-184">REMARKS</span></span>|<span data-ttu-id="524a5-185">String</span><span class="sxs-lookup"><span data-stu-id="524a5-185">String</span></span>|  
|<span data-ttu-id="524a5-186">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="524a5-186">COLUMN_DEF</span></span>|<span data-ttu-id="524a5-187">String</span><span class="sxs-lookup"><span data-stu-id="524a5-187">String</span></span>|  
|<span data-ttu-id="524a5-188">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-188">SQL_DATA_TYPE</span></span>|<span data-ttu-id="524a5-189">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-189">Int16</span></span>|  
|<span data-ttu-id="524a5-190">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="524a5-190">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="524a5-191">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-191">Int16</span></span>|  
|<span data-ttu-id="524a5-192">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="524a5-192">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="524a5-193">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-193">Int32</span></span>|  
|<span data-ttu-id="524a5-194">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="524a5-194">ORDINAL_POSITION</span></span>|<span data-ttu-id="524a5-195">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-195">Int32</span></span>|  
|<span data-ttu-id="524a5-196">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="524a5-196">IS_NULLABLE</span></span>|<span data-ttu-id="524a5-197">String</span><span class="sxs-lookup"><span data-stu-id="524a5-197">String</span></span>|  
|<span data-ttu-id="524a5-198">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="524a5-198">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="524a5-199">String</span><span class="sxs-lookup"><span data-stu-id="524a5-199">String</span></span>|  
|<span data-ttu-id="524a5-200">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="524a5-200">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="524a5-201">String</span><span class="sxs-lookup"><span data-stu-id="524a5-201">String</span></span>|  
|<span data-ttu-id="524a5-202">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-202">SS_DATA_TYPE</span></span>|<span data-ttu-id="524a5-203">Byte</span><span class="sxs-lookup"><span data-stu-id="524a5-203">Byte</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="524a5-204">Procedury</span><span class="sxs-lookup"><span data-stu-id="524a5-204">Procedures</span></span>  
  
|<span data-ttu-id="524a5-205">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="524a5-205">ColumnName</span></span>|<span data-ttu-id="524a5-206">Datový typ</span><span class="sxs-lookup"><span data-stu-id="524a5-206">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="524a5-207">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="524a5-207">PROCEDURE_CAT</span></span>|<span data-ttu-id="524a5-208">String</span><span class="sxs-lookup"><span data-stu-id="524a5-208">String</span></span>|  
|<span data-ttu-id="524a5-209">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="524a5-209">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="524a5-210">String</span><span class="sxs-lookup"><span data-stu-id="524a5-210">String</span></span>|  
|<span data-ttu-id="524a5-211">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-211">PROCEDURE_NAME</span></span>|<span data-ttu-id="524a5-212">String</span><span class="sxs-lookup"><span data-stu-id="524a5-212">String</span></span>|  
|<span data-ttu-id="524a5-213">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="524a5-213">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="524a5-214">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-214">Int32</span></span>|  
|<span data-ttu-id="524a5-215">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="524a5-215">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="524a5-216">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-216">Int32</span></span>|  
|<span data-ttu-id="524a5-217">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="524a5-217">NUM_RESULT_SETS</span></span>|<span data-ttu-id="524a5-218">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-218">Int32</span></span>|  
|<span data-ttu-id="524a5-219">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="524a5-219">REMARKS</span></span>|<span data-ttu-id="524a5-220">String</span><span class="sxs-lookup"><span data-stu-id="524a5-220">String</span></span>|  
|<span data-ttu-id="524a5-221">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-221">PROCEDURE_TYPE</span></span>|<span data-ttu-id="524a5-222">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-222">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="524a5-223">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="524a5-223">ProcedureColumns</span></span>  
  
|<span data-ttu-id="524a5-224">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="524a5-224">ColumnName</span></span>|<span data-ttu-id="524a5-225">Datový typ</span><span class="sxs-lookup"><span data-stu-id="524a5-225">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="524a5-226">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="524a5-226">PROCEDURE_CAT</span></span>|<span data-ttu-id="524a5-227">String</span><span class="sxs-lookup"><span data-stu-id="524a5-227">String</span></span>|  
|<span data-ttu-id="524a5-228">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="524a5-228">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="524a5-229">String</span><span class="sxs-lookup"><span data-stu-id="524a5-229">String</span></span>|  
|<span data-ttu-id="524a5-230">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-230">PROCEDURE_NAME</span></span>|<span data-ttu-id="524a5-231">String</span><span class="sxs-lookup"><span data-stu-id="524a5-231">String</span></span>|  
|<span data-ttu-id="524a5-232">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-232">COLUMN_NAME</span></span>|<span data-ttu-id="524a5-233">String</span><span class="sxs-lookup"><span data-stu-id="524a5-233">String</span></span>|  
|<span data-ttu-id="524a5-234">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-234">COLUMN_TYPE</span></span>|<span data-ttu-id="524a5-235">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-235">Int16</span></span>|  
|<span data-ttu-id="524a5-236">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-236">DATA_TYPE</span></span>|<span data-ttu-id="524a5-237">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-237">Int16</span></span>|  
|<span data-ttu-id="524a5-238">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-238">TYPE_NAME</span></span>|<span data-ttu-id="524a5-239">String</span><span class="sxs-lookup"><span data-stu-id="524a5-239">String</span></span>|  
|<span data-ttu-id="524a5-240">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="524a5-240">COLUMN_SIZE</span></span>|<span data-ttu-id="524a5-241">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-241">Int32</span></span>|  
|<span data-ttu-id="524a5-242">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="524a5-242">BUFFER_LENGTH</span></span>|<span data-ttu-id="524a5-243">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-243">Int32</span></span>|  
|<span data-ttu-id="524a5-244">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="524a5-244">DECIMAL_DIGITS</span></span>|<span data-ttu-id="524a5-245">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-245">Int16</span></span>|  
|<span data-ttu-id="524a5-246">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="524a5-246">NUM_PREC_RADIX</span></span>|<span data-ttu-id="524a5-247">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-247">Int16</span></span>|  
|<span data-ttu-id="524a5-248">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="524a5-248">NULLABLE</span></span>|<span data-ttu-id="524a5-249">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-249">Int16</span></span>|  
|<span data-ttu-id="524a5-250">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="524a5-250">REMARKS</span></span>|<span data-ttu-id="524a5-251">String</span><span class="sxs-lookup"><span data-stu-id="524a5-251">String</span></span>|  
|<span data-ttu-id="524a5-252">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="524a5-252">COLUMN_DEF</span></span>|<span data-ttu-id="524a5-253">String</span><span class="sxs-lookup"><span data-stu-id="524a5-253">String</span></span>|  
|<span data-ttu-id="524a5-254">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-254">SQL_DATA_TYPE</span></span>|<span data-ttu-id="524a5-255">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-255">Int16</span></span>|  
|<span data-ttu-id="524a5-256">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="524a5-256">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="524a5-257">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-257">Int16</span></span>|  
|<span data-ttu-id="524a5-258">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="524a5-258">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="524a5-259">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-259">Int32</span></span>|  
|<span data-ttu-id="524a5-260">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="524a5-260">ORDINAL_POSITION</span></span>|<span data-ttu-id="524a5-261">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-261">Int32</span></span>|  
|<span data-ttu-id="524a5-262">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="524a5-262">IS_NULLABLE</span></span>|<span data-ttu-id="524a5-263">String</span><span class="sxs-lookup"><span data-stu-id="524a5-263">String</span></span>|  
|<span data-ttu-id="524a5-264">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="524a5-264">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="524a5-265">String</span><span class="sxs-lookup"><span data-stu-id="524a5-265">String</span></span>|  
|<span data-ttu-id="524a5-266">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="524a5-266">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="524a5-267">String</span><span class="sxs-lookup"><span data-stu-id="524a5-267">String</span></span>|  
|<span data-ttu-id="524a5-268">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-268">SS_DATA_TYPE</span></span>|<span data-ttu-id="524a5-269">Byte</span><span class="sxs-lookup"><span data-stu-id="524a5-269">Byte</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="524a5-270">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="524a5-270">ProcedureParameters</span></span>  
  
|<span data-ttu-id="524a5-271">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="524a5-271">ColumnName</span></span>|<span data-ttu-id="524a5-272">Datový typ</span><span class="sxs-lookup"><span data-stu-id="524a5-272">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="524a5-273">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="524a5-273">PROCEDURE_CAT</span></span>|<span data-ttu-id="524a5-274">String</span><span class="sxs-lookup"><span data-stu-id="524a5-274">String</span></span>|  
|<span data-ttu-id="524a5-275">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="524a5-275">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="524a5-276">String</span><span class="sxs-lookup"><span data-stu-id="524a5-276">String</span></span>|  
|<span data-ttu-id="524a5-277">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-277">PROCEDURE_NAME</span></span>|<span data-ttu-id="524a5-278">String</span><span class="sxs-lookup"><span data-stu-id="524a5-278">String</span></span>|  
|<span data-ttu-id="524a5-279">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-279">COLUMN_NAME</span></span>|<span data-ttu-id="524a5-280">String</span><span class="sxs-lookup"><span data-stu-id="524a5-280">String</span></span>|  
|<span data-ttu-id="524a5-281">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-281">COLUMN_TYPE</span></span>|<span data-ttu-id="524a5-282">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-282">Int16</span></span>|  
|<span data-ttu-id="524a5-283">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-283">DATA_TYPE</span></span>|<span data-ttu-id="524a5-284">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-284">Int16</span></span>|  
|<span data-ttu-id="524a5-285">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-285">TYPE_NAME</span></span>|<span data-ttu-id="524a5-286">String</span><span class="sxs-lookup"><span data-stu-id="524a5-286">String</span></span>|  
|<span data-ttu-id="524a5-287">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="524a5-287">COLUMN_SIZE</span></span>|<span data-ttu-id="524a5-288">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-288">Int32</span></span>|  
|<span data-ttu-id="524a5-289">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="524a5-289">BUFFER_LENGTH</span></span>|<span data-ttu-id="524a5-290">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-290">Int32</span></span>|  
|<span data-ttu-id="524a5-291">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="524a5-291">DECIMAL_DIGITS</span></span>|<span data-ttu-id="524a5-292">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-292">Int16</span></span>|  
|<span data-ttu-id="524a5-293">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="524a5-293">NUM_PREC_RADIX</span></span>|<span data-ttu-id="524a5-294">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-294">Int16</span></span>|  
|<span data-ttu-id="524a5-295">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="524a5-295">NULLABLE</span></span>|<span data-ttu-id="524a5-296">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-296">Int16</span></span>|  
|<span data-ttu-id="524a5-297">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="524a5-297">REMARKS</span></span>|<span data-ttu-id="524a5-298">String</span><span class="sxs-lookup"><span data-stu-id="524a5-298">String</span></span>|  
|<span data-ttu-id="524a5-299">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="524a5-299">COLUMN_DEF</span></span>|<span data-ttu-id="524a5-300">String</span><span class="sxs-lookup"><span data-stu-id="524a5-300">String</span></span>|  
|<span data-ttu-id="524a5-301">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-301">SQL_DATA_TYPE</span></span>|<span data-ttu-id="524a5-302">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-302">Int16</span></span>|  
|<span data-ttu-id="524a5-303">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="524a5-303">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="524a5-304">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-304">Int16</span></span>|  
|<span data-ttu-id="524a5-305">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="524a5-305">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="524a5-306">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-306">Int32</span></span>|  
|<span data-ttu-id="524a5-307">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="524a5-307">ORDINAL_POSITION</span></span>|<span data-ttu-id="524a5-308">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-308">Int32</span></span>|  
|<span data-ttu-id="524a5-309">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="524a5-309">IS_NULLABLE</span></span>|<span data-ttu-id="524a5-310">String</span><span class="sxs-lookup"><span data-stu-id="524a5-310">String</span></span>|  
|<span data-ttu-id="524a5-311">SS_TYPE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="524a5-311">SS_TYPE_CATALOG</span></span>|<span data-ttu-id="524a5-312">String</span><span class="sxs-lookup"><span data-stu-id="524a5-312">String</span></span>|  
|<span data-ttu-id="524a5-313">SS_TYPE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="524a5-313">SS_TYPE_SCHEMA</span></span>|<span data-ttu-id="524a5-314">String</span><span class="sxs-lookup"><span data-stu-id="524a5-314">String</span></span>|  
|<span data-ttu-id="524a5-315">SS_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-315">SS_DATA_TYPE</span></span>|<span data-ttu-id="524a5-316">Byte</span><span class="sxs-lookup"><span data-stu-id="524a5-316">Byte</span></span>|  
  
## <a name="microsoft-oracle-odbc-driver"></a><span data-ttu-id="524a5-317">Ovladač ODBC Microsoft Oracle</span><span class="sxs-lookup"><span data-stu-id="524a5-317">Microsoft Oracle ODBC Driver</span></span>  
 <span data-ttu-id="524a5-318">Ovladače ODBC Microsoft SQL Server Oracle podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="524a5-318">The Microsoft SQL Server Oracle ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="524a5-319">Tabulky</span><span class="sxs-lookup"><span data-stu-id="524a5-319">Tables</span></span>  
  
-   <span data-ttu-id="524a5-320">Sloupce</span><span class="sxs-lookup"><span data-stu-id="524a5-320">Columns</span></span>  
  
-   <span data-ttu-id="524a5-321">Procedury</span><span class="sxs-lookup"><span data-stu-id="524a5-321">Procedures</span></span>  
  
-   <span data-ttu-id="524a5-322">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="524a5-322">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="524a5-323">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="524a5-323">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="524a5-324">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="524a5-324">Views</span></span>  
  
-   <span data-ttu-id="524a5-325">Indexy</span><span class="sxs-lookup"><span data-stu-id="524a5-325">Indexes</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="524a5-326">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="524a5-326">Tables and Views</span></span>  
  
|<span data-ttu-id="524a5-327">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="524a5-327">ColumnName</span></span>|<span data-ttu-id="524a5-328">Datový typ</span><span class="sxs-lookup"><span data-stu-id="524a5-328">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="524a5-329">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="524a5-329">TABLE_QUALIFIER</span></span>|<span data-ttu-id="524a5-330">String</span><span class="sxs-lookup"><span data-stu-id="524a5-330">String</span></span>|  
|<span data-ttu-id="524a5-331">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="524a5-331">TABLE_OWNER</span></span>|<span data-ttu-id="524a5-332">String</span><span class="sxs-lookup"><span data-stu-id="524a5-332">String</span></span>|  
|<span data-ttu-id="524a5-333">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-333">TABLE_NAME</span></span>|<span data-ttu-id="524a5-334">String</span><span class="sxs-lookup"><span data-stu-id="524a5-334">String</span></span>|  
|<span data-ttu-id="524a5-335">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-335">TABLE_TYPE</span></span>|<span data-ttu-id="524a5-336">String</span><span class="sxs-lookup"><span data-stu-id="524a5-336">String</span></span>|  
|<span data-ttu-id="524a5-337">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="524a5-337">REMARKS</span></span>|<span data-ttu-id="524a5-338">String</span><span class="sxs-lookup"><span data-stu-id="524a5-338">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="524a5-339">Sloupce</span><span class="sxs-lookup"><span data-stu-id="524a5-339">Columns</span></span>  
  
|<span data-ttu-id="524a5-340">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="524a5-340">ColumnName</span></span>|<span data-ttu-id="524a5-341">Datový typ</span><span class="sxs-lookup"><span data-stu-id="524a5-341">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="524a5-342">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="524a5-342">TABLE_QUALIFIER</span></span>|<span data-ttu-id="524a5-343">String</span><span class="sxs-lookup"><span data-stu-id="524a5-343">String</span></span>|  
|<span data-ttu-id="524a5-344">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="524a5-344">TABLE_OWNER</span></span>|<span data-ttu-id="524a5-345">String</span><span class="sxs-lookup"><span data-stu-id="524a5-345">String</span></span>|  
|<span data-ttu-id="524a5-346">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-346">TABLE_NAME</span></span>|<span data-ttu-id="524a5-347">String</span><span class="sxs-lookup"><span data-stu-id="524a5-347">String</span></span>|  
|<span data-ttu-id="524a5-348">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-348">COLUMN_NAME</span></span>|<span data-ttu-id="524a5-349">String</span><span class="sxs-lookup"><span data-stu-id="524a5-349">String</span></span>|  
|<span data-ttu-id="524a5-350">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-350">DATA_TYPE</span></span>|<span data-ttu-id="524a5-351">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-351">Int16</span></span>|  
|<span data-ttu-id="524a5-352">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-352">TYPE_NAME</span></span>|<span data-ttu-id="524a5-353">String</span><span class="sxs-lookup"><span data-stu-id="524a5-353">String</span></span>|  
|<span data-ttu-id="524a5-354">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="524a5-354">PRECISION</span></span>|<span data-ttu-id="524a5-355">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-355">Int32</span></span>|  
|<span data-ttu-id="524a5-356">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="524a5-356">LENGTH</span></span>|<span data-ttu-id="524a5-357">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-357">Int32</span></span>|  
|<span data-ttu-id="524a5-358">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="524a5-358">SCALE</span></span>|<span data-ttu-id="524a5-359">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-359">Int16</span></span>|  
|<span data-ttu-id="524a5-360">RADIX</span><span class="sxs-lookup"><span data-stu-id="524a5-360">RADIX</span></span>|<span data-ttu-id="524a5-361">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-361">Int16</span></span>|  
|<span data-ttu-id="524a5-362">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="524a5-362">NULLABLE</span></span>|<span data-ttu-id="524a5-363">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-363">Int16</span></span>|  
|<span data-ttu-id="524a5-364">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="524a5-364">REMARKS</span></span>|<span data-ttu-id="524a5-365">String</span><span class="sxs-lookup"><span data-stu-id="524a5-365">String</span></span>|  
|<span data-ttu-id="524a5-366">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="524a5-366">ORDINAL_POSITION</span></span>|<span data-ttu-id="524a5-367">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-367">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="524a5-368">Procedury</span><span class="sxs-lookup"><span data-stu-id="524a5-368">Procedures</span></span>  
  
|<span data-ttu-id="524a5-369">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="524a5-369">ColumnName</span></span>|<span data-ttu-id="524a5-370">Datový typ</span><span class="sxs-lookup"><span data-stu-id="524a5-370">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="524a5-371">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="524a5-371">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="524a5-372">String</span><span class="sxs-lookup"><span data-stu-id="524a5-372">String</span></span>|  
|<span data-ttu-id="524a5-373">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="524a5-373">PROCEDURE_OWNER</span></span>|<span data-ttu-id="524a5-374">String</span><span class="sxs-lookup"><span data-stu-id="524a5-374">String</span></span>|  
|<span data-ttu-id="524a5-375">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-375">PROCEDURE_NAME</span></span>|<span data-ttu-id="524a5-376">String</span><span class="sxs-lookup"><span data-stu-id="524a5-376">String</span></span>|  
|<span data-ttu-id="524a5-377">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="524a5-377">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="524a5-378">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-378">Int16</span></span>|  
|<span data-ttu-id="524a5-379">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="524a5-379">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="524a5-380">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-380">Int16</span></span>|  
|<span data-ttu-id="524a5-381">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="524a5-381">NUM_RESULT_SETS</span></span>|<span data-ttu-id="524a5-382">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-382">Int16</span></span>|  
|<span data-ttu-id="524a5-383">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="524a5-383">REMARKS</span></span>|<span data-ttu-id="524a5-384">String</span><span class="sxs-lookup"><span data-stu-id="524a5-384">String</span></span>|  
|<span data-ttu-id="524a5-385">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-385">PROCEDURE_TYPE</span></span>|<span data-ttu-id="524a5-386">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-386">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="524a5-387">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="524a5-387">ProcedureColumns</span></span>  
  
|<span data-ttu-id="524a5-388">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="524a5-388">ColumnName</span></span>|<span data-ttu-id="524a5-389">Datový typ</span><span class="sxs-lookup"><span data-stu-id="524a5-389">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="524a5-390">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="524a5-390">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="524a5-391">String</span><span class="sxs-lookup"><span data-stu-id="524a5-391">String</span></span>|  
|<span data-ttu-id="524a5-392">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="524a5-392">PROCEDURE_OWNER</span></span>|<span data-ttu-id="524a5-393">String</span><span class="sxs-lookup"><span data-stu-id="524a5-393">String</span></span>|  
|<span data-ttu-id="524a5-394">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-394">PROCEDURE_NAME</span></span>|<span data-ttu-id="524a5-395">String</span><span class="sxs-lookup"><span data-stu-id="524a5-395">String</span></span>|  
|<span data-ttu-id="524a5-396">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-396">COLUMN_NAME</span></span>|<span data-ttu-id="524a5-397">String</span><span class="sxs-lookup"><span data-stu-id="524a5-397">String</span></span>|  
|<span data-ttu-id="524a5-398">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-398">COLUMN_TYPE</span></span>|<span data-ttu-id="524a5-399">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-399">Int16</span></span>|  
|<span data-ttu-id="524a5-400">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-400">DATA_TYPE</span></span>|<span data-ttu-id="524a5-401">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-401">Int16</span></span>|  
|<span data-ttu-id="524a5-402">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-402">TYPE_NAME</span></span>|<span data-ttu-id="524a5-403">String</span><span class="sxs-lookup"><span data-stu-id="524a5-403">String</span></span>|  
|<span data-ttu-id="524a5-404">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="524a5-404">PRECISION</span></span>|<span data-ttu-id="524a5-405">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-405">Int32</span></span>|  
|<span data-ttu-id="524a5-406">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="524a5-406">LENGTH</span></span>|<span data-ttu-id="524a5-407">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-407">Int32</span></span>|  
|<span data-ttu-id="524a5-408">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="524a5-408">SCALE</span></span>|<span data-ttu-id="524a5-409">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-409">Int16</span></span>|  
|<span data-ttu-id="524a5-410">RADIX</span><span class="sxs-lookup"><span data-stu-id="524a5-410">RADIX</span></span>|<span data-ttu-id="524a5-411">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-411">Int16</span></span>|  
|<span data-ttu-id="524a5-412">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="524a5-412">NULLABLE</span></span>|<span data-ttu-id="524a5-413">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-413">Int16</span></span>|  
|<span data-ttu-id="524a5-414">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="524a5-414">REMARKS</span></span>|<span data-ttu-id="524a5-415">String</span><span class="sxs-lookup"><span data-stu-id="524a5-415">String</span></span>|  
|<span data-ttu-id="524a5-416">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="524a5-416">OVERLOAD</span></span>|<span data-ttu-id="524a5-417">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-417">Int32</span></span>|  
|<span data-ttu-id="524a5-418">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="524a5-418">ORDINAL_POSITION</span></span>|<span data-ttu-id="524a5-419">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-419">Int32</span></span>|  
  
## <a name="microsoft-jet-odbc-driver"></a><span data-ttu-id="524a5-420">Ovladač ODBC Microsoft Jet</span><span class="sxs-lookup"><span data-stu-id="524a5-420">Microsoft Jet ODBC Driver</span></span>  
 <span data-ttu-id="524a5-421">Ovladač ODBC Microsoft Jet podporuje následující kolekce určité schéma kromě společné kolekce schémat:</span><span class="sxs-lookup"><span data-stu-id="524a5-421">The Microsoft Jet ODBC Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="524a5-422">Tabulky</span><span class="sxs-lookup"><span data-stu-id="524a5-422">Tables</span></span>  
  
-   <span data-ttu-id="524a5-423">Indexy</span><span class="sxs-lookup"><span data-stu-id="524a5-423">Indexes</span></span>  
  
-   <span data-ttu-id="524a5-424">Sloupce</span><span class="sxs-lookup"><span data-stu-id="524a5-424">Columns</span></span>  
  
-   <span data-ttu-id="524a5-425">Procedury</span><span class="sxs-lookup"><span data-stu-id="524a5-425">Procedures</span></span>  
  
-   <span data-ttu-id="524a5-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="524a5-426">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="524a5-427">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="524a5-427">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="524a5-428">Zobrazení</span><span class="sxs-lookup"><span data-stu-id="524a5-428">Views</span></span>  
  
### <a name="tables-and-views"></a><span data-ttu-id="524a5-429">Tabulky a zobrazení</span><span class="sxs-lookup"><span data-stu-id="524a5-429">Tables and Views</span></span>  
  
|<span data-ttu-id="524a5-430">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="524a5-430">ColumnName</span></span>|<span data-ttu-id="524a5-431">Datový typ</span><span class="sxs-lookup"><span data-stu-id="524a5-431">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="524a5-432">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="524a5-432">TABLE_QUALIFIER</span></span>|<span data-ttu-id="524a5-433">String</span><span class="sxs-lookup"><span data-stu-id="524a5-433">String</span></span>|  
|<span data-ttu-id="524a5-434">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="524a5-434">TABLE_OWNER</span></span>|<span data-ttu-id="524a5-435">String</span><span class="sxs-lookup"><span data-stu-id="524a5-435">String</span></span>|  
|<span data-ttu-id="524a5-436">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-436">TABLE_NAME</span></span>|<span data-ttu-id="524a5-437">String</span><span class="sxs-lookup"><span data-stu-id="524a5-437">String</span></span>|  
|<span data-ttu-id="524a5-438">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-438">TABLE_TYPE</span></span>|<span data-ttu-id="524a5-439">String</span><span class="sxs-lookup"><span data-stu-id="524a5-439">String</span></span>|  
|<span data-ttu-id="524a5-440">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="524a5-440">REMARKS</span></span>|<span data-ttu-id="524a5-441">String</span><span class="sxs-lookup"><span data-stu-id="524a5-441">String</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="524a5-442">Sloupce</span><span class="sxs-lookup"><span data-stu-id="524a5-442">Columns</span></span>  
  
|<span data-ttu-id="524a5-443">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="524a5-443">ColumnName</span></span>|<span data-ttu-id="524a5-444">Datový typ</span><span class="sxs-lookup"><span data-stu-id="524a5-444">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="524a5-445">TABLE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="524a5-445">TABLE_QUALIFIER</span></span>|<span data-ttu-id="524a5-446">String</span><span class="sxs-lookup"><span data-stu-id="524a5-446">String</span></span>|  
|<span data-ttu-id="524a5-447">TABLE_OWNER</span><span class="sxs-lookup"><span data-stu-id="524a5-447">TABLE_OWNER</span></span>|<span data-ttu-id="524a5-448">String</span><span class="sxs-lookup"><span data-stu-id="524a5-448">String</span></span>|  
|<span data-ttu-id="524a5-449">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-449">TABLE_NAME</span></span>|<span data-ttu-id="524a5-450">String</span><span class="sxs-lookup"><span data-stu-id="524a5-450">String</span></span>|  
|<span data-ttu-id="524a5-451">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-451">COLUMN_NAME</span></span>|<span data-ttu-id="524a5-452">String</span><span class="sxs-lookup"><span data-stu-id="524a5-452">String</span></span>|  
|<span data-ttu-id="524a5-453">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-453">DATA_TYPE</span></span>|<span data-ttu-id="524a5-454">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-454">Int16</span></span>|  
|<span data-ttu-id="524a5-455">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-455">TYPE_NAME</span></span>|<span data-ttu-id="524a5-456">String</span><span class="sxs-lookup"><span data-stu-id="524a5-456">String</span></span>|  
|<span data-ttu-id="524a5-457">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="524a5-457">PRECISION</span></span>|<span data-ttu-id="524a5-458">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-458">Int32</span></span>|  
|<span data-ttu-id="524a5-459">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="524a5-459">LENGTH</span></span>|<span data-ttu-id="524a5-460">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-460">Int32</span></span>|  
|<span data-ttu-id="524a5-461">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="524a5-461">SCALE</span></span>|<span data-ttu-id="524a5-462">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-462">Int16</span></span>|  
|<span data-ttu-id="524a5-463">RADIX</span><span class="sxs-lookup"><span data-stu-id="524a5-463">RADIX</span></span>|<span data-ttu-id="524a5-464">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-464">Int16</span></span>|  
|<span data-ttu-id="524a5-465">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="524a5-465">NULLABLE</span></span>|<span data-ttu-id="524a5-466">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-466">Int16</span></span>|  
|<span data-ttu-id="524a5-467">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="524a5-467">REMARKS</span></span>|<span data-ttu-id="524a5-468">String</span><span class="sxs-lookup"><span data-stu-id="524a5-468">String</span></span>|  
|<span data-ttu-id="524a5-469">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="524a5-469">ORDINAL_POSITION</span></span>|<span data-ttu-id="524a5-470">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-470">Int32</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="524a5-471">Procedury</span><span class="sxs-lookup"><span data-stu-id="524a5-471">Procedures</span></span>  
  
|<span data-ttu-id="524a5-472">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="524a5-472">ColumnName</span></span>|<span data-ttu-id="524a5-473">Datový typ</span><span class="sxs-lookup"><span data-stu-id="524a5-473">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="524a5-474">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="524a5-474">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="524a5-475">String</span><span class="sxs-lookup"><span data-stu-id="524a5-475">String</span></span>|  
|<span data-ttu-id="524a5-476">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="524a5-476">PROCEDURE_OWNER</span></span>|<span data-ttu-id="524a5-477">String</span><span class="sxs-lookup"><span data-stu-id="524a5-477">String</span></span>|  
|<span data-ttu-id="524a5-478">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-478">PROCEDURE_NAME</span></span>|<span data-ttu-id="524a5-479">String</span><span class="sxs-lookup"><span data-stu-id="524a5-479">String</span></span>|  
|<span data-ttu-id="524a5-480">NUM_INPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="524a5-480">NUM_INPUT_PARAMS</span></span>|<span data-ttu-id="524a5-481">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-481">Int16</span></span>|  
|<span data-ttu-id="524a5-482">NUM_OUTPUT_PARAMS</span><span class="sxs-lookup"><span data-stu-id="524a5-482">NUM_OUTPUT_PARAMS</span></span>|<span data-ttu-id="524a5-483">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-483">Int16</span></span>|  
|<span data-ttu-id="524a5-484">NUM_RESULT_SETS</span><span class="sxs-lookup"><span data-stu-id="524a5-484">NUM_RESULT_SETS</span></span>|<span data-ttu-id="524a5-485">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-485">Int16</span></span>|  
|<span data-ttu-id="524a5-486">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="524a5-486">REMARKS</span></span>|<span data-ttu-id="524a5-487">String</span><span class="sxs-lookup"><span data-stu-id="524a5-487">String</span></span>|  
|<span data-ttu-id="524a5-488">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-488">PROCEDURE_TYPE</span></span>|<span data-ttu-id="524a5-489">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-489">Int16</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="524a5-490">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="524a5-490">ProcedureColumns</span></span>  
  
|<span data-ttu-id="524a5-491">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="524a5-491">ColumnName</span></span>|<span data-ttu-id="524a5-492">Datový typ</span><span class="sxs-lookup"><span data-stu-id="524a5-492">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="524a5-493">PROCEDURE_QUALIFIER</span><span class="sxs-lookup"><span data-stu-id="524a5-493">PROCEDURE_QUALIFIER</span></span>|<span data-ttu-id="524a5-494">String</span><span class="sxs-lookup"><span data-stu-id="524a5-494">String</span></span>|  
|<span data-ttu-id="524a5-495">PROCEDURE_OWNER</span><span class="sxs-lookup"><span data-stu-id="524a5-495">PROCEDURE_OWNER</span></span>|<span data-ttu-id="524a5-496">String</span><span class="sxs-lookup"><span data-stu-id="524a5-496">String</span></span>|  
|<span data-ttu-id="524a5-497">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-497">PROCEDURE_NAME</span></span>|<span data-ttu-id="524a5-498">String</span><span class="sxs-lookup"><span data-stu-id="524a5-498">String</span></span>|  
|<span data-ttu-id="524a5-499">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-499">COLUMN_NAME</span></span>|<span data-ttu-id="524a5-500">String</span><span class="sxs-lookup"><span data-stu-id="524a5-500">String</span></span>|  
|<span data-ttu-id="524a5-501">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-501">COLUMN_TYPE</span></span>|<span data-ttu-id="524a5-502">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-502">Int16</span></span>|  
|<span data-ttu-id="524a5-503">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-503">DATA_TYPE</span></span>|<span data-ttu-id="524a5-504">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-504">Int16</span></span>|  
|<span data-ttu-id="524a5-505">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-505">TYPE_NAME</span></span>|<span data-ttu-id="524a5-506">String</span><span class="sxs-lookup"><span data-stu-id="524a5-506">String</span></span>|  
|<span data-ttu-id="524a5-507">PŘESNOST</span><span class="sxs-lookup"><span data-stu-id="524a5-507">PRECISION</span></span>|<span data-ttu-id="524a5-508">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-508">Int32</span></span>|  
|<span data-ttu-id="524a5-509">DÉLKA</span><span class="sxs-lookup"><span data-stu-id="524a5-509">LENGTH</span></span>|<span data-ttu-id="524a5-510">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-510">Int32</span></span>|  
|<span data-ttu-id="524a5-511">ŠKÁLOVÁNÍ</span><span class="sxs-lookup"><span data-stu-id="524a5-511">SCALE</span></span>|<span data-ttu-id="524a5-512">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-512">Int16</span></span>|  
|<span data-ttu-id="524a5-513">RADIX</span><span class="sxs-lookup"><span data-stu-id="524a5-513">RADIX</span></span>|<span data-ttu-id="524a5-514">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-514">Int16</span></span>|  
|<span data-ttu-id="524a5-515">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="524a5-515">NULLABLE</span></span>|<span data-ttu-id="524a5-516">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-516">Int16</span></span>|  
|<span data-ttu-id="524a5-517">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="524a5-517">REMARKS</span></span>|<span data-ttu-id="524a5-518">String</span><span class="sxs-lookup"><span data-stu-id="524a5-518">String</span></span>|  
|<span data-ttu-id="524a5-519">PŘETÍŽENÍ</span><span class="sxs-lookup"><span data-stu-id="524a5-519">OVERLOAD</span></span>|<span data-ttu-id="524a5-520">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-520">Int32</span></span>|  
|<span data-ttu-id="524a5-521">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="524a5-521">ORDINAL_POSITION</span></span>|<span data-ttu-id="524a5-522">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-522">Int32</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="524a5-523">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="524a5-523">ProcedureParameters</span></span>  
  
|<span data-ttu-id="524a5-524">Názevsloupce</span><span class="sxs-lookup"><span data-stu-id="524a5-524">ColumnName</span></span>|<span data-ttu-id="524a5-525">Datový typ</span><span class="sxs-lookup"><span data-stu-id="524a5-525">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="524a5-526">PROCEDURE_CAT</span><span class="sxs-lookup"><span data-stu-id="524a5-526">PROCEDURE_CAT</span></span>|<span data-ttu-id="524a5-527">String</span><span class="sxs-lookup"><span data-stu-id="524a5-527">String</span></span>|  
|<span data-ttu-id="524a5-528">PROCEDURE_SCHEM</span><span class="sxs-lookup"><span data-stu-id="524a5-528">PROCEDURE_SCHEM</span></span>|<span data-ttu-id="524a5-529">String</span><span class="sxs-lookup"><span data-stu-id="524a5-529">String</span></span>|  
|<span data-ttu-id="524a5-530">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-530">PROCEDURE_NAME</span></span>|<span data-ttu-id="524a5-531">String</span><span class="sxs-lookup"><span data-stu-id="524a5-531">String</span></span>|  
|<span data-ttu-id="524a5-532">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-532">COLUMN_NAME</span></span>|<span data-ttu-id="524a5-533">String</span><span class="sxs-lookup"><span data-stu-id="524a5-533">String</span></span>|  
|<span data-ttu-id="524a5-534">COLUMN_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-534">COLUMN_TYPE</span></span>|<span data-ttu-id="524a5-535">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-535">Int16</span></span>|  
|<span data-ttu-id="524a5-536">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-536">DATA_TYPE</span></span>|<span data-ttu-id="524a5-537">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-537">Int16</span></span>|  
|<span data-ttu-id="524a5-538">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="524a5-538">TYPE_NAME</span></span>|<span data-ttu-id="524a5-539">String</span><span class="sxs-lookup"><span data-stu-id="524a5-539">String</span></span>|  
|<span data-ttu-id="524a5-540">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="524a5-540">COLUMN_SIZE</span></span>|<span data-ttu-id="524a5-541">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-541">Int32</span></span>|  
|<span data-ttu-id="524a5-542">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="524a5-542">BUFFER_LENGTH</span></span>|<span data-ttu-id="524a5-543">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-543">Int32</span></span>|  
|<span data-ttu-id="524a5-544">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="524a5-544">DECIMAL_DIGITS</span></span>|<span data-ttu-id="524a5-545">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-545">Int16</span></span>|  
|<span data-ttu-id="524a5-546">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="524a5-546">NUM_PREC_RADIX</span></span>|<span data-ttu-id="524a5-547">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-547">Int16</span></span>|  
|<span data-ttu-id="524a5-548">S POVOLENOU HODNOTOU NULL</span><span class="sxs-lookup"><span data-stu-id="524a5-548">NULLABLE</span></span>|<span data-ttu-id="524a5-549">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-549">Int16</span></span>|  
|<span data-ttu-id="524a5-550">POZNÁMKY</span><span class="sxs-lookup"><span data-stu-id="524a5-550">REMARKS</span></span>|<span data-ttu-id="524a5-551">String</span><span class="sxs-lookup"><span data-stu-id="524a5-551">String</span></span>|  
|<span data-ttu-id="524a5-552">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="524a5-552">COLUMN_DEF</span></span>|<span data-ttu-id="524a5-553">String</span><span class="sxs-lookup"><span data-stu-id="524a5-553">String</span></span>|  
|<span data-ttu-id="524a5-554">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="524a5-554">SQL_DATA_TYPE</span></span>|<span data-ttu-id="524a5-555">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-555">Int16</span></span>|  
|<span data-ttu-id="524a5-556">SQL_DATETIME_SUB</span><span class="sxs-lookup"><span data-stu-id="524a5-556">SQL_DATETIME_SUB</span></span>|<span data-ttu-id="524a5-557">Int16</span><span class="sxs-lookup"><span data-stu-id="524a5-557">Int16</span></span>|  
|<span data-ttu-id="524a5-558">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="524a5-558">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="524a5-559">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-559">Int32</span></span>|  
|<span data-ttu-id="524a5-560">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="524a5-560">ORDINAL_POSITION</span></span>|<span data-ttu-id="524a5-561">Int32</span><span class="sxs-lookup"><span data-stu-id="524a5-561">Int32</span></span>|  
|<span data-ttu-id="524a5-562">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="524a5-562">IS_NULLABLE</span></span>|<span data-ttu-id="524a5-563">String</span><span class="sxs-lookup"><span data-stu-id="524a5-563">String</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="524a5-564">Viz také</span><span class="sxs-lookup"><span data-stu-id="524a5-564">See Also</span></span>  
 [<span data-ttu-id="524a5-565">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="524a5-565">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
