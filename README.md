# SQLmap
sqlmap is an open source penetration testing tool that automates the process of detecting and exploiting SQL injection flaws and taking over of database



![image-removebg-preview](https://github.com/HackWithSumit/SQLmap/assets/120317751/f8cc59b9-3efe-420f-9c79-de3870822763)




Basic Command:

1. Crawling for SQL Inject Parameters.

Command: 

       sqlmap -u altor.testfire.php --crawl <1-3>
     
     
2. To get the Database name, we use 
  
       sqlmap -u altor.testfire.php --crawl <1-3> --dbs
       
 
 3. To get the tables name, we use command --tables. In this case we have to replace the --dbs with -D 'Database-name'

 4. Get the columns name. For that we'll use command --columns. In this case we have to replace the --dbs with -D & --tables with -T 

<b>To get the database names and details. </b>

5. To dump the tables/contents. Use command --dump. 


Google Dork SQL Injection:

https://gbhackers.com/latest-google-sql-dorks/


Extra Features:
--------------------------------------------------------------

1. Thread: To increase the concurrent users attacking simultanously. Range 1-10

2. Risk: If we want to increase the risk or different type of queries. Ex: Update/Delete/Insert etc. Range 1-3

3. Level: To increase the different parameters for SQL injection attack. Command --level 1-5

4. Verbosity: We can view the detailed request which is being sent by sqlmap. 
Command: -v 0-6

Example:

[17:04:37] [TRAFFIC OUT] HTTP request [#25]:
GET http://testphp.vulnweb.com/Mod_Rewrite_Shop/Details/color-printer/3/ HTTP/1.1
Cache-control: no-cache
User-agent: sqlmap/1.6.6.4#dev (https://sqlmap.org)
Host: testphp.vulnweb.com
Accept: */*
Accept-encoding: gzip,deflate
Connection: close


GET / HTTP/1.1
Referrer: xyz.com
User-agent: GECKO_Chrome 
Host: testphp.vulnweb.com
Accept: */*
Accept-encoding: gzip,deflate
Connection: close


5. Output: we can use --output-dir <path> or we can use > <path>

6. mobile: To trick server thinking that request is being sent from a mobile phone.

which smartphone do you want sqlmap to imitate through HTTP User-Agent header?
[1] Apple iPhone 8 (default)
[2] BlackBerry Z10
[3] Google Nexus 7
[4] Google Pixel
[5] HP iPAQ 6365
[6] HTC 10
[7] Huawei P8
[8] Microsoft Lumia 950
[9] Nokia N97
[10] Samsung Galaxy S8
[11] Xiaomi Mi 8 Pro


7. Tamper List: It is used to bypass the firewall by encoding the keywords, command “sqlmap –list-tampers”. It can be used using command —tamper=<tamper type>. Example: --tamper=base64encode.



listing available tamper scripts

* 0eunion.py - Replaces instances of <int> UNION with <int>e0UNION
* apostrophemask.py - Replaces apostrophe character (') with its UTF-8 full width counterpart (e.g. ' -> %EF%BC%87)
* apostrophenullencode.py - Replaces apostrophe character (') with its illegal double unicode counterpart (e.g. ' -> %00%27)
* appendnullbyte.py - Appends (Access) NULL byte character (%00) at the end of payload
* base64encode.py - Base64-encodes all characters in a given payload
* between.py - Replaces greater than operator ('>') with 'NOT BETWEEN 0 AND #' and equals operator ('=') with 'BETWEEN # AND #'
* binary.py - Injects keyword binary where possible
* bluecoat.py - Replaces space character after SQL statement with a valid random blank character. Afterwards replace character '=' with operator LIKE
* chardoubleencode.py - Double URL-encodes all characters in a given payload (not processing already encoded) (e.g. SELECT -> %2553%2545%254C%2545%2543%2554)
* charencode.py - URL-encodes all characters in a given payload (not processing already encoded) (e.g. SELECT -> %53%45%4C%45%43%54)
* charunicodeencode.py - Unicode-URL-encodes all characters in a given payload (not processing already encoded) (e.g. SELECT -> %u0053%u0045%u004C%u0045%u0043%u0054)
* charunicodeescape.py - Unicode-escapes non-encoded characters in a given payload (not processing already encoded) (e.g. SELECT -> \u0053\u0045\u004C\u0045\u0043\u0054)
* commalesslimit.py - Replaces (MySQL) instances like 'LIMIT M, N' with 'LIMIT N OFFSET M' counterpart
* commalessmid.py - Replaces (MySQL) instances like 'MID(A, B, C)' with 'MID(A FROM B FOR C)' counterpart
* commentbeforeparentheses.py - Prepends (inline) comment before parentheses (e.g. ( -> /**/()
* concat2concatws.py - Replaces (MySQL) instances like 'CONCAT(A, B)' with 'CONCAT_WS(MID(CHAR(0), 0, 0), A, B)' counterpart
* dunion.py - Replaces instances of <int> UNION with <int>DUNION
* equaltolike.py - Replaces all occurrences of operator equal ('=') with 'LIKE' counterpart
* equaltorlike.py - Replaces all occurrences of operator equal ('=') with 'RLIKE' counterpart
* escapequotes.py - Slash escape single and double quotes (e.g. ' -> \')
* greatest.py - Replaces greater than operator ('>') with 'GREATEST' counterpart
* halfversionedmorekeywords.py - Adds (MySQL) versioned comment before each keyword
* hex2char.py - Replaces each (MySQL) 0x<hex> encoded string with equivalent CONCAT(CHAR(),...) counterpart
* htmlencode.py - HTML encode (using code points) all non-alphanumeric characters (e.g. ' -> &#39;)
* ifnull2casewhenisnull.py - Replaces instances like 'IFNULL(A, B)' with 'CASE WHEN ISNULL(A) THEN (B) ELSE (A) END' counterpart
* ifnull2ifisnull.py - Replaces instances like 'IFNULL(A, B)' with 'IF(ISNULL(A), B, A)' counterpart
* informationschemacomment.py - Add an inline comment (/**/) to the end of all occurrences of (MySQL) "information_schema" identifier
* least.py - Replaces greater than operator ('>') with 'LEAST' counterpart
* lowercase.py - Replaces each keyword character with lower case value (e.g. SELECT -> select)
* luanginx.py - LUA-Nginx WAFs Bypass (e.g. Cloudflare)
* misunion.py - Replaces instances of UNION with -.1UNION
* modsecurityversioned.py - Embraces complete query with (MySQL) versioned comment
* modsecurityzeroversioned.py - Embraces complete query with (MySQL) zero-versioned comment
* multiplespaces.py - Adds multiple spaces (' ') around SQL keywords
* ord2ascii.py - Replaces ORD() occurences with equivalent ASCII() calls
* overlongutf8.py - Converts all (non-alphanum) characters in a given payload to overlong UTF8 (not processing already encoded) (e.g. ' -> %C0%A7)
* overlongutf8more.py - Converts all characters in a given payload to overlong UTF8 (not processing already encoded) (e.g. SELECT -> %C1%93%C1%85%C1%8C%C1%85%C1%83%C1%94)
* percentage.py - Adds a percentage sign ('%') infront of each character (e.g. SELECT -> %S%E%L%E%C%T)
* plus2concat.py - Replaces plus operator ('+') with (MsSQL) function CONCAT() counterpart
* plus2fnconcat.py - Replaces plus operator ('+') with (MsSQL) ODBC function {fn CONCAT()} counterpart
* randomcase.py - Replaces each keyword character with random case value (e.g. SELECT -> SEleCt)
* randomcomments.py - Add random inline comments inside SQL keywords (e.g. SELECT -> S/**/E/**/LECT)
* schemasplit.py - Splits FROM schema identifiers (e.g. 'testdb.users') with whitespace (e.g. 'testdb 9.e.users')
* sleep2getlock.py - Replaces instances like 'SLEEP(5)' with (e.g.) "GET_LOCK('ETgP',5)"
* sp_password.py - Appends (MsSQL) function 'sp_password' to the end of the payload for automatic obfuscation from DBMS logs
* space2comment.py - Replaces space character (' ') with comments '/**/'
* space2dash.py - Replaces space character (' ') with a dash comment ('--') followed by a random string and a new line ('\n')
* space2hash.py - Replaces (MySQL) instances of space character (' ') with a pound character ('#') followed by a random string and a new line ('\n')
* space2morecomment.py - Replaces (MySQL) instances of space character (' ') with comments '/**_**/'
* space2morehash.py - Replaces (MySQL) instances of space character (' ') with a pound character ('#') followed by a random string and a new line ('\n')
* space2mssqlblank.py - Replaces (MsSQL) instances of space character (' ') with a random blank character from a valid set of alternate characters
* space2mssqlhash.py - Replaces space character (' ') with a pound character ('#') followed by a new line ('\n')
* space2mysqlblank.py - Replaces (MySQL) instances of space character (' ') with a random blank character from a valid set of alternate characters
* space2mysqldash.py - Replaces space character (' ') with a dash comment ('--') followed by a new line ('\n')
* space2plus.py - Replaces space character (' ') with plus ('+')
* space2randomblank.py - Replaces space character (' ') with a random blank character from a valid set of alternate characters
* substring2leftright.py - Replaces PostgreSQL SUBSTRING with LEFT and RIGHT
* symboliclogical.py - Replaces AND and OR logical operators with their symbolic counterparts (&& and ||)
* unionalltounion.py - Replaces instances of UNION ALL SELECT with UNION SELECT counterpart
* unmagicquotes.py - Replaces quote character (') with a multi-byte combo %BF%27 together with generic comment at the end (to make it work)
* uppercase.py - Replaces each keyword character with upper case value (e.g. select -> SELECT)
* varnish.py - Appends a HTTP header 'X-originating-IP' to bypass Varnish Firewall
* versionedkeywords.py - Encloses each non-function keyword with (MySQL) versioned comment
* versionedmorekeywords.py - Encloses each keyword with (MySQL) versioned comment
* xforwardedfor.py - Append a fake HTTP header 'X-Forwarded-For' (and alike)



       
