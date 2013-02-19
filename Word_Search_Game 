'''A board is a list of list of str. For example, the board
    ANTT
    XSOB
is represented as the list
    [['A', 'N', 'T', 'T'], ['X', 'S', 'O', 'B']]

A word list is a list of str. For example, the list of words
    ANT
    BOX
    SOB
    TO
is represented as the list
    ['ANT', 'BOX', 'SOB', 'TO']
'''


def is_valid_word(wordlist, word):
    ''' (list of str, str) -> bool

    Return True if and only if word is an element of wordlist.

    >>> is_valid_word(['ANT', 'BOX', 'SOB', 'TO'], 'TO')
    True
    '''
    found = False
    for str in wordlist:
        if word in wordlist:
            found = True
    return found

def make_str_from_row(board, row_index):
    ''' (list of list of str, int) -> str

    Return the characters from the row of the board with index row_index
    as a single string.

    >>> make_str_from_row([['A', 'N', 'T', 'T'], ['X', 'S', 'O', 'B']], 0)
    'ANTT'
    '''
    row_string = ''
    for index in board[row_index]:
        row_string = row_string + index
    return row_string
    
def make_str_from_column(board, column_index):
    ''' (list of list of str, int) -> str

    Return the characters from the column of the board with index column_index
    as a single string.

    >>> make_str_from_column([['A', 'N', 'T', 'T'], ['X', 'S', 'O', 'B']], 1)
    'NS'
    '''

    col_string = ''
    for index in board:
        for col_index in index[column_index]:
           col_string = col_string + col_index
    return col_string

def board_contains_word_in_row(board, word):
    ''' (list of list of str, str) -> bool

    Return True if and only if one or more of the rows of the board contains
    word.

    Precondition: board has at least one row and one column, and word is a
    valid word.

    >>> board_contains_word_in_row([['A', 'N', 'T', 'T'], ['X', 'S', 'O', 'B']], 'SOB')
    True
    '''

    for row_index in range(len(board)):
        if word in make_str_from_row(board, row_index):
            return True

    return False

def board_contains_word_in_column(board, word):
    ''' (list of list of str, str) -> bool

    Return True if and only if one or more of the columns of the board
    contains word.

    Precondition: board has at least one row and one column, and word is a
    valid word.

    >>> board_contains_word_in_column([['A', 'N', 'T', 'T'], ['X', 'S', 'O', 'B']], 'NO')
    False
    '''

    for column_index in range(len(board[0])):
        if word in make_str_from_column(board, column_index):
            return True
    return False


def board_contains_word(board, word):
    '''(list of list of str, str) -> bool

    Return True if and only if word appears in board.

    Precondition: board has at least one row and one column.

    >>> board_contains_word([['A', 'N', 'T', 'T'], ['X', 'S', 'O', 'B']], 'ANT')
    True
    '''

    if board_contains_word_in_column(board, word) or board_contains_word_in_row(board, word):
        return True
    else:
        return False
        
def word_score(word):
    '''(str) -> int

    Return the point value the word earns.

    Word length: < 3: 0 points
                 3-6: 1 point per character in word
                 7-9: 2 points per character in word
                 10+: 3 points per character in word

    >>> word_score('DRUDGERY')
    16
    '''
    point = 0
    if board_contains_word:
        if len(word) < 3:
            point = point
        elif len(word) >= 3 and len(word) <= 6:
            for chr in word:
                point = point + 1
        elif len(word) >= 7 and len(word) <= 9:
            for chr in word:
                point = point + 2
        elif len(word) >= 10:
            for chr in word:
                point = point + 3
    return point

def update_score(player_info, word):
    '''([str, int] list, str) -> NoneType

    player_info is a list with the player's name and score. Update player_info
    by adding the point value word earns to the player's score.

    >>> update_score(['Jonathan', 4], 'ANT')
    ''' 
    for each in range(1,len(player_info)):
        player_info[1] = player_info[1] + word_score(word)
    return None
        
def num_words_on_board(board, words):
    '''(list of list of str, list of str) -> int

    Return how many words appear on board.

    >>> num_words_on_board([['A', 'N', 'T', 'T'], ['X', 'S', 'O', 'B']], ['ANT', 'BOX', 'SOB', 'TO'])
    3
    '''
    num = 0
    for chr in words:
        if board_contains_word(board, chr):
                num = num + 1
    return num

def read_words(words_file):
    ''' (file open for reading) -> list of str

    Return a list of all words (with newlines removed) from open file
    words_file.

    Precondition: Each line of the file contains a word in uppercase characters
    from the standard English alphabet.
    '''
    words = []
    for line in words_file:
        words.append(line.rstrip('\n'))
    words_file.close()
    return words
    
def read_board(board_file):
    ''' (file open for reading) -> list of list of str

    Return a board read from open file board_file. The board file will contain
    one row of the board per line. Newlines are not included in the board.
    '''
    
    count = 0
    lst = []
    for line in board_file:
            count = count + 1
            lst.append(line.rstrip('\n'))
    lst_words = [[] for i in range(count)]

    for each in range(count):
       for ie in lst[each]:
           for chr in ie:
               lst_words[each].append(chr)
    board_file.close()
    return lst_words  
